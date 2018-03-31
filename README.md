# RxJavaHelloWorld

Reactive Hello world application in android

Adding RxJava 2 library  to a Java project in Android Studio
To use RxJava in a Gradle build, add the following as dependency.

compile group: 'io.reactivex.rxjava2', name: 'rxjava', version: '2.1.1'
For Maven, you can add RxJava via the following snippet.

<dependency>
    <groupId>io.reactivex.rxjava2</groupId>
    <artifactId>rxjava</artifactId>
    <version>2.0.4</version>
</dependency>
STEP 1:

Declare an observable data items first

Observable<String> observable = Observable.just("Hello ", " World");
STEP 2

Create an Observer like this

Observer<String> stringObserver = new Observer<String>() {
    @Override
    public void onSubscribe(Disposable d) {
        Log.d(TAG, "onSubscribe() called with: d = [" + d + "]");
    }

    @Override
    public void onNext(String s) {
        Log.d(TAG, "onNext() called with: s = [" + s + "]");
        appCompatTextView.setText(String.format("%s%s", appCompatTextView.getText().toString(), s));
    }

    @Override
    public void onError(Throwable e) {
        Log.d(TAG, "onError() called with: e = [" + e + "]");
    }

    @Override
    public void onComplete() {
        Log.d(TAG, "onComplete() called");
    }
};

There Are four methods implement when create an Observer

onSubscribe(Disposable d)
onNext(String s)
onError(Throwable e)
onComplete()
When Subscribing  onSubscribe called first time that observer is subscribed observable data,After that onNext called twice returning string items,When completed items onComplete called and transaction completed. If any error occurs onError called .

STEP 3:

Subscribe Observable Using Observer created above.

observable.subscribe(stringObserver);
After Subscribing onNext(String s) called two times  because we put two string items in observable

in onNext(String s)  we setting text to a textview.





Thanks Happy coding :D

