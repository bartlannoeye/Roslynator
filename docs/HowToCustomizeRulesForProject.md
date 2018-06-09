# How to: Customize Rules for a Project

It is common that you have in you solution one rule set that is shared across all projects (global.ruleset).

It is also common that you want to disable/enable certain analyzer in one or more (but not all) projects.

## Example: Disable Analyzer in a Project

Let's say you would like to disable rule **RCS1090** in a project 'AspNetCoreProject' which uses rule set global.ruleset.

1) Create a new rule set file called 'project.ruleset' with following content:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ASP.NET Core" ToolsVersion="15.0">
  <Include Path="relative_or_absolute_path_to_global_ruleset" Action="Default" />
  <Rules AnalyzerId="Roslynator.CSharp.Analyzers" RuleNamespace="Roslynator.CSharp.Analyzers">
    <Rule Id="RCS1090" Action="None" />
  </Rules>
</RuleSet>
```

2) Update AspNetCoreProject.csproj so it uses project.ruleset instead of global.ruleset.

Now **RCS1090** is disabled in AspNetCoreProject and all other rules are inherited from global.ruleset.
