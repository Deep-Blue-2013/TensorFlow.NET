# 	Get started with TensorFlow.NET

让我们先运行一个经典的HelloWorld程序，看看TensorFlow在.NET上面运行的效果，我想不出有比做个HelloWorld更简单的方式了。

Let's run a classic HelloWorld program first and see if TensorFlow is running on .NET. I can't think of a simpler way to be a HelloWorld.

### Install the TensorFlow.NET SDK 安装开发环境

TensorFlow.NET uses the .NET Standard 2.0 standard, so your new project Target Framework can be .NET Framework or .NET Core.  All the examples in this book are using .NET Core 2.2 and Microsoft Visual Studio Community 2017. To start building TensorFlow program you just need to download and install the .NET SDK (Software Development Kit). You have to download the latest .NET Core SDK from offical website: https://dotnet.microsoft.com/download.

TensorFlow.NET采用.NET标准库2.0版本，因此你的新建工程可以是.NET Framework或者是基于.NET Core的。本文中的所有例子都是用的.NET Core 2.2的，IDE用的是Microsoft Visual Studio Community 2017。为了能编译和运行TensorFlow工程，你需要从这里下载最新的.NET Core SDK: https://dotnet.microsoft.com/download。

1. New a project

   ![New Project](_static/new-project.png)

2. Choose Console App (.NET Core)

   ![Console App](_static/new-project-console.png)



```cmd
PM> Install-Package TensorFlow.NET
```

### Start coding Hello World 开始编写Hello World

After installing the TensorFlow.NET package, you can use the `using Tensorflow` to introduce the TensorFlow library.

安装完TensorFlow.NET包后，你就可以使用`using Tensorflow`来引入TensorFlow库了。

```csharp
using System;
using Tensorflow;

namespace TensorFlowNET.Examples
{
    /// <summary>
    /// Simple hello world using TensorFlow
    /// </summary>
    public class HelloWorld : IExample
    {
        public void Run()
        {
            /* Create a Constant op
               The op is added as a node to the default graph.
            
               The value returned by the constructor represents the output
               of the Constant op. */
            var hello = tf.constant("Hello, TensorFlow!");

            // Start tf session
            using (var sess = tf.Session())
            {
                // Run the op
                var result = sess.run(hello);
                Console.WriteLine(result);
            }
        }
    }
}
```
After CTRL + F5 run, you will get the output.
```cmd
2019-01-05 10:53:42.145931: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2
Hello, TensorFlow!
Press any key to continue . . .
```

