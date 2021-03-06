# PowerShell cmdlet in C# example

This repo is here simply to show off how you can create a simple PowerShell Core (cross platform) cmdlet in C# and unit test it with xUnit in a .Net Core test project, and is a companion sample to [my blog post](https://blog.danskingdom.com/Create-and-test-PowerShell-Core-cmdlets-in-CSharp/) that describes the process.

We use the [Microsoft.PowerShell.SDK](https://www.nuget.org/packages/Microsoft.PowerShell.SDK/) NuGet package in the xUnit test project, which allows us to invoke the cmdlet.

## Be careful with test project reference

As I pointed out in [my Stack Overflow question](https://stackoverflow.com/questions/56696574/how-to-unit-test-a-powershell-core-binary-cmdlet-in-c-sharp), several blogs/tutorials tell you to use the `PowerShellStandard.Library` NuGet package in your test project to get a .Net Core version of the `System.Management.Automation` assembly. This is the assembly you use to run unit tests against PowerShell cmdlets in .Net Framework, however, that .Net Core NuGet package does not work properly and simply throws an exception when trying invoke cmdlets in your unit tests with it, so be sure to avoid it.

## More info

Microsoft has [posted a new blog](https://devblogs.microsoft.com/powershell/depending-on-the-right-powershell-nuget-package-in-your-net-project/) that describes the various PowerShell project types, which one to use when, and which NuGet packages to include.
