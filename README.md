
# Hello World CSharp 

## In Powershell, doing a dotnet compile 
cd C:\Users\lawle\Documents\dotnet\C#\Code\HelloWorldCSharp

code . 

dotnet run

-- TEST - use call operator to run executable 
& C:\Users\lawle\Documents\dotnet\C#\Code\HelloWorldCSharp\bin\Debug\netcoreapp3.1\HelloWorldCSharp.exe 


## In Powershell, doing a manual compile using csc.exe 
-- Note no need for csproj file 
-- Location 
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe 
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe 

-- compile command 
C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe /t:exe /out:HelloWorldCSharpMan.exe Program.cs 
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe /t:exe /out:HelloWorldCSharpMan.exe Program.cs 

-- Compile text; limited to C# 5.0 only. 
This compiler is provided as part of the Microsoft (R) .NET Framework, but only supports language versions up to C# 5, which is no longer the latest version. For compilers that support newer versions of the C# programming language, see http://go.microsoft.com/fwlink/?LinkID=533240

-- TESTING 
-- Call operator with explict path 
& C:\Users\lawle\Documents\dotnet\C#\Code\HelloWorldCSharp\HelloWorldCSharpMan.exe

-- Call operator with current directory  
& .\HelloWorldCSharpMan.exe

-- Invoke-Expression
$exp = ".\HelloWorldCSharpMan.exe"
Invoke-Expression $exp 

-- Invoke-Command (ICM)  (seems to keep running, but no output) 
$scriptblock = {& .\HelloWorldCSharpMan.exe}
Invoke-Command -scriptblock $scriptblock -computername "lawlermj1" 

-- old cmd shell - replaces & 
cmd /c .\HelloWorldCSharpMan.exe

-- Start-Process  - getting stdout and stderr is a whole script - do later 
Start-Process .\HelloWorldCSharpMan.exe 
-> no error, but no output  
Start-Process .\HelloWorldCSharpMan.exe -PassThru
-> shows process info like handles, etc 

-- Error ; only if csproj included. 
HelloWorldCSharp.csproj(1,1): error CS0116: A namespace cannot directly contain members such as fields or methods
