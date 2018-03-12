# CSharp-client-for-TensorFlow
Access a TensorFlow service from a c# client using the gRPC protocol

# Overview
Using a trained TensorFlow network in in a python or java environment or even building an android app is well documented and there are lots of examples which will pave you the way.

But poor programmer when it comes to access a TensorFlow server from a c# application.

One core task herby is to build c# classes based on the “protobuf” templates to communicate with the TensorFlow service based on the gRPC protocol.

What we finally want to accomplish is to provide c# classes, which we can use in our c# client to communicate with the service.
This code may look like this:

```<language>
private void button_Click(object _sender, RoutedEventArgs _e)
{
Channel channel = new Channel("127.0.0.1:50051",ChannelCredentials.Insecure);
PredictionService.PredictionServiceClient client = new PredictionService.PredictionServiceClient(channel);

PredictRequest request = new PredictRequest();
request.ModelSpec.Name = "inception";
request.ModelSpec.SignatureName = "predict_images";
request.Inputs["images"] = null;

PredictResponse response = client.Predict(request);
}
```
------------

# Collecting the tools and protobuf templates

To make TensorFlow clients more general, the needed classes are defined in so called protobuf files.
These are templates based on which code for languages like java, python, c, c# etc. can be generated.
The tool to generate the code classes is the protobuf compiler “protoc.exe”.

The required protobuf templates can be categorized in
1) gRPC protocol support
2) TensorFlow support
3) Application specific 

For this “cookbook” i  already have collected all the necessary protobuf templates together with their dependencies in the folder protocol_buffer_files and the compiler along with it's resources in protocol_compiler.

# Usage
After downloading the repository simply switch to the folder protocol_compiler and call "protoc.bat". This will generate the c# classes into the output folder cs_classes.

# This example will soon be continued...







