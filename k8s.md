# 自定义controller
下载code-generate   
```
./code-generator/generate-groups.sh all k8s.io/test-controller/pkg/generated  k8s.io/test-controller/pkg/apis example:v1
```
生成controller核心代码    
下载sample-controller

```
func main() {

	flag.Parse()

	// set up signals so we handle the first shutdown signal gracefully
	stopCh := signals.SetupSignalHandler()

	cfg, err := clientcmd.BuildConfigFromFlags(masterURL, kubeconfig)

	if err != nil {
		klog.Fatalf("Error building kubeconfig: %s", err.Error())
	}

	kubeClient, err := kubernetes.NewForConfig(cfg)
	if err != nil {
		klog.Fatalf("Error building kubernetes clientset: %s", err.Error())
	}

	run := func(ctx context.Context) {

		fmt.Println("leader start")


		exampleClient, err := clientset.NewForConfig(cfg)
		if err != nil {
			klog.Fatalf("Error building example clientset: %s", err.Error())
		}

		kubeInformerFactory := kubeinformers.NewSharedInformerFactory(kubeClient, time.Second*30)
		exampleInformerFactory := informers.NewSharedInformerFactory(exampleClient, time.Second*30)

		contro := controller.NewController(kubeClient, exampleClient,
			kubeInformerFactory.Apps().V1().Deployments(),
			kubeInformerFactory.Core().V1().Pods(),
			exampleInformerFactory.Example().V1().TestTypes())

		// notice that there is no need to run Start methods in a separate goroutine. (i.e. go kubeInformerFactory.Start(stopCh)
		// Start method is non-blocking and runs all registered informers in a dedicated goroutine.
		kubeInformerFactory.Start(stopCh)
		exampleInformerFactory.Start(stopCh)

		if err = contro.Run(2, stopCh); err != nil {
			klog.Fatalf("Error running controller: %s", err.Error())
		}
	}

	rl, err := resourcelock.New(resourcelock.EndpointsResourceLock,
		"yincong",
		"test-controller",
		kubeClient.CoreV1(),
		kubeClient.CoordinationV1(),
		resourcelock.ResourceLockConfig{
			Identity: string(uuid.NewUUID()),
		})
	if err != nil {
		klog.Fatalf("error creating lock: %v", err)
	}

	leaderelection.RunOrDie(context.TODO(), leaderelection.LeaderElectionConfig{
		Lock:          rl,
		LeaseDuration: 3 * time.Second, // 需要续时的间隔 3s没续时就国企高管
		RenewDeadline: 2 * time.Second, // 需要续时的时间 2s续一次
		RetryPeriod:   1 * time.Second, // 续时失败第二次续时的时间间隔
		Callbacks: leaderelection.LeaderCallbacks{
			OnStartedLeading: run,
			OnStoppedLeading: func() {
				klog.Fatalf("leaderelection lost")
			},
		},
		Name: "test-controller",
	})
}
```
这事main函数的写法，主要是使用选主功能   

其他部分同sample-controller    
