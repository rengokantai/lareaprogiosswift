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
##4. Take Things Further
###1 Use forward delegates
####01:39
```
model.data.bindTo(tableView.rx_itemsWithDataSource(dataSource)).addDisposableTo(disposeBag)
```
