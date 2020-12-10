# About
DataPort (tentative title) is an open source package, which simplifies data-focused communication by eliminating boilerplate code and providing fast, secure and reliable way to transmit arbitrary amounts of data. It is intended as a dead simple way of exposing machine learning models, but could be used for any data transmission task.
Features:
- Fast binary protocol over TCP
- Out-of-the-box encryption
- Compression
- Numpy support

# Installation

## Python
```shell script
pip install dataport
```

## Android (Java and Kotlin)
```
dependencies {
    ...
    implementation 'com.vialai.android:dataport:1.1'
}
```

## SWIFT (Xcode)
Select `File > Swift Packages > Add Package Dependency` and enter `https://github.com/VialAI/dataport-ios`.

# Examples
Ask yourself how many times you coded something like this, and it turned out to be not so quick and simple to implement, as it seemed initially?

## Server

```python
import dataport

s = dataport.server(name='object-detector', port=8080, secret='kl3erjjldsfk', ondata=lambda x: model.predict(x.data))
s.serve()
```


## Client (Python)

```python
import dataport
import cv2

port = dataport.create(uri='https://server:8080/object-detector', secret='kl3erjjldsfk')

cap = cv2.VideoCapture(0)

while frame:=cap.read()[1]:
	result = port.process(frame)
	print(f'Class: {result.data[0, np.argmax(result.data[0,:])]} Latency: {result.latency}')
```

## Client (Kotlin)

## Client (SWIFT)

