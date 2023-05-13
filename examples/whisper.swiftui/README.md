A sample SwiftUI app using [whisper.cpp](https://github.com/ggerganov/whisper.cpp/) to do voice-to-text transcriptions.
See also: [whisper.objc](https://github.com/ggerganov/whisper.cpp/tree/master/examples/whisper.objc).

**Usage**:

1. Select a model from the [whisper.cpp repository](https://github.com/ggerganov/whisper.cpp/tree/master/models).[^1]
2. Add the model to `whisper.swiftui.demo/Resources/models` **via Xcode**.
3. Select a sample audio file (for example, [jfk.wav](https://github.com/ggerganov/whisper.cpp/raw/master/samples/jfk.wav)).
4. Add the sample audio file to `whisper.swiftui.demo/Resources/samples` **via Xcode**.
5. Select the "Release" [^2] build configuration under "Run", then deploy and run to your device.

**CoreML**:

To test with CoreML:

![image2](https://github.com/ggerganov/whisper.cpp/assets/898335/7047b853-b8ce-4460-961b-3920768e6d48)

Add your `mlmodelc` file to the `Models` directory. Make sure it is named correctly for Whisper.cpp to see it. For example, `ggml-base.bin` should be `ggml-base-encoder.mlmodelc`

To enable CoreML in source projects, you need to include the `CoreML` source files in your project, and set your Preprocessor Headers to include `WHISPER_USE_COREML`

![image3](https://github.com/ggerganov/whisper.cpp/assets/898335/74b2c548-8d8e-451e-9c38-a29bba512620)

**Note:** Pay attention to the folder path: `whisper.swiftui.demo/Resources/models` is the appropriate directory to place resources whilst `whisper.swiftui.demo/Models` is related to actual code.

[^1]: I recommend the tiny, base or small models for running on an iOS device.

[^2]: The `Release` build can boost performance of transcription. In this project, it also added `-O3 -DNDEBUG` to `Other C Flags`, but adding flags to app proj is not ideal in real world (applies to all C/C++ files), consider splitting xcodeproj in workspace in your own project.

![image](https://user-images.githubusercontent.com/1991296/212539216-0aef65e4-f882-480a-8358-0f816838fd52.png)
