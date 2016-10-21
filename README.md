# lareaprogiosswift
##2. Introduction
###1 Observable sequences
####02:00
```
exampleOf("just"){
  let observable = Observable.just("hello")
  observable.subscribe{
    event in print(event)
  }
}
```
print
```
Next(hello)
Completed
```

####03:13
```
exampleOf("of"){
  let observable = Observable.of(1,2,3)
  observable.subscribe{
    print($0)
  }
}
```
print
```
Next(1)
Next(2)
Next(3)
Completed
```
####05:00
```
exampleOf("toObservable"){
 [1,2,3].toObservable().subscribeNext{
    print($0)
  }
}
```
print
```
1
2
3
```
####06:05 DisposeBag  and Disposable
```
exampleOf("toObservable"){
  let DisposeBag = DisposeBag()
 let subscription:Disposable=[1,2,3].toObservable().subscribeNext{
    print($0)
  }
  
  subscription.addDisposableTo(disppposeBag)
}
```

####07:00 subscribeCompleted
```
exampleOf("toObservable"){
  let DisposeBag = DisposeBag()
 let subscription:Disposable=[1,2,3].toObservable().subscribeCompleted{
    print("Complated")
  }
  
  subscription.addDisposableTo(disppposeBag)
}
```


###2 Work with subjects
####01:00 PublishSubject
```
exampleOf("Publish Subject"){
  let subject = PublishSubject<String>()
  subject.subscribe{
    print($0)
  }
  subject.on(.Next("hello"))
  subject.onCompleted()
  subject.onNext("hello")
}
```
print
```
"Hello"
"world"
```
Once a completed event is emitted, an observable sequence is terminated.



####04:40 BehaviorSubject
```
exampleOf("BehaviorSubject"){
  let subject = BehaviorSubject(value:"a")
  let firstSubscription = subject.subscribeNext{
    print(#line, $0)
  }
  subject.onNext("b")
   let secondtSubscription = subject.subscribeNext{
    print(#line, $0)
  }
}
```

####05:30 ReplaySubject
```
exampleOf("ReplaySubject"){
  let subject = ReplaySubject<Int>.create(bufferSize(2)
  subject.onNext(1)
  subject.onNext(2)
  subject.onNext(2)
  subject.subscribeNext{
    print($0)
  }
}
```

####06:40 Variable
```
exampleOf("Variable"){
  let variable = Variable("A")
  variable.asObservable().subscribeNext{print($0)}
  variab;e.value="B"
}
```
print
```
A
B
```


###3 Transform observable sequences
####01:00
```
exampleOf("map"){
  Observable.of(1,2,3)
  .map({$0*$0}
  .subscribeNext{print($0)}
  .dispose()
   
  
}
```

####02:39
```
exampleOf("flatMap"){
  let disposeBag = DisposeBag()
  struct Player{
    let score:Variable<Int>
  }
  let a = Player(score:Variable(10))
  let b = Player(score:Variable(20))
  var player =Variable(a)
  
}
```





##4. Take Things Further
###1 Use forward delegates
####01:39
```
model.data.bindTo(tableView.rx_itemsWithDataSource(dataSource)).addDisposableTo(disposeBag)
```
