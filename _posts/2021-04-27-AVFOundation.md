---
title: 1.AVFoundation
excerpt: iOS


#최상위 사진
header:
  #image: /assets/images/moon3.png
  teaser: /assets/images/moon3-th.png

gallery:
  - url: /assets/images/unsplash-gallery-image-1.jpg
    image_path: assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
  - url: /assets/images/unsplash-gallery-image-2.jpg
    image_path: assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
  - url: /assets/images/unsplash-gallery-image-3.jpg
    image_path: assets/images/unsplash-gallery-image-3-th.jpg
    alt: "placeholder image 3"
    


 #사이드바 설정 
sidebar:
  - title: "Role"
    nav: sidebar-sample

# 해당 글 목차
toc: true
toc_sticky: true

toc_label: "Yimsu's Blog"
toc_icon: "cog"


## 테그설정

categories:
  - iOS

tags:
  - iOS_Basic
  - "2021"
  - "2021.04"



---


### 1. NSString

<br/>

- A static, plain-text Unicode string object that bridges to `String`

- use `NSString` when you need reference semantics or other Foundation-specific behavior

<br/>

<br/>



### 2. NSObject

<br>

The root class of most Objective-C class hierarchies, from which subclasses inherit a basic interface to the runtime system and the ability to behave as Objective-C objects.

<br/>

<br/>

### 3. AVFoundation 

AVFoundation - 시각 청각 미디어 자료를 플레이하고 생성하는 프레임워크.

<br/>

![image](/assets/images/computervision/210427.png)

<br/>

#### 3.1 AVURLAsset 

 `AVURLAsset` is a concrete subclass of [`AVAsset`](https://developer.apple.com/documentation/avfoundation/avasset). When you create an asset as shown below, you’re actually creating an [`AVURLAsset`](https://developer.apple.com/documentation/avfoundation/avurlasset) instance.



#### 3.2 AVAssetExportSession 

An object that transcodes the contents of an asset source object to create an output of the form described by a specified export preset.











``` swif	

  open func cropVideoWithUrl(videoUrl url: URL, startTime: CGFloat, duration: CGFloat, completion: ((_ videoPath: URL?, _ error: NSError?) -> Void)?) {
    
    DispatchQueue.global().async {
      let asset = AVURLAsset(url: url, options: nil)
      let exportSession = AVAssetExportSession(asset: asset, presetName: "AVAssetExportPresetHighestQuality")
      let paths: NSArray = NSSearchPathForDirectoriesInDomains(.documentDirectory, .userDomainMask, true) as NSArray
      var outputURL = paths.object(at: 0) as! String
      let manager = FileManager.default
        
        
      do {
        try manager.createDirectory(atPath: outputURL, withIntermediateDirectories: true, attributes: nil)
      } catch _ {
      }
        
      outputURL = outputURL.convert.appendingPathComponent("output.mp4")
      
      do {
        try manager.removeItem(atPath: outputURL)
      } catch _ {
      }
        
        
      if let exportSession = exportSession as AVAssetExportSession? {
        exportSession.outputURL = URL(fileURLWithPath: outputURL)
        exportSession.shouldOptimizeForNetworkUse = true
        exportSession.outputFileType = AVFileType.mp4
        let start = CMTimeMakeWithSeconds(Float64(startTime), preferredTimescale: 600)
        let duration = CMTimeMakeWithSeconds(Float64(duration), preferredTimescale: 600)
        let range = CMTimeRangeMake(start: start, duration: duration)
        
        exportSession.timeRange = range
        
        exportSession.exportAsynchronously { () -> Void in
          
          switch exportSession.status {
          case AVAssetExportSessionStatus.completed:
            completion?(exportSession.outputURL, nil)
          case AVAssetExportSessionStatus.failed:
            print("Failed: \(String(describing: exportSession.error))")
          case AVAssetExportSessionStatus.cancelled:
            print("Failed: \(String(describing: exportSession.error))")
          default:
            print("default case")
          }
            
        }
      }
        
        
      DispatchQueue.main.async {
      }
    }
  }
}


```
