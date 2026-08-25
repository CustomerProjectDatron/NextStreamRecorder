# CameraStreamRecorder

This module allows recording video streams from cameras directly within the Next software environment.

The main features are the following:

- Connect to various types of cameras ( Overview, Needle, Webcam)
- Record video streams and save them in different formats
- Record multiple streams simultaneously
- Capture a single snapshot image from a camera stream

## Usage

The recording works with handles to the camera streams. This allows starting and stopping recordings independently for each stream.
To start recording a camera stream, use the `StartCameraRecording` function, providing the camera handle and the desired output file path. To stop the recording, use the `StopCameraRecording` function with the same camera handle.

```simpl
# import the CameraStreamRecorder module
import CameraStreamRecorder

# start recording the Overview camera stream
record1 = CameraStreamRecorder::StartRecording filename="TestRecordOverview" compress  Overview

# do all the stuff you want to record...

CameraStreamRecorder::StopRecording recordId=ref record1
```

The file ending and format will be set automatically based on the compression settings. Non compressed _.avi and compressed _.mp4.

In the end thats all you need to do to record camera streams.

## Taking a single snapshot

If you only need a single picture instead of a video, use `CaptureImage`. It does not need a handle or a stop call - it blocks until the picture has been taken and saved.

```simpl
# import the CameraStreamRecorder module
import CameraStreamRecorder

# take a single picture from the webcam and store it as "TestImage.jpg"
CameraStreamRecorder::CaptureImage filename="TestImage" Webcam
```

The image is always stored as `.jpg`, the file ending is added automatically.

