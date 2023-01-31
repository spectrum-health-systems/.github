# Abatab XML documentation guidelines

* When possible, link to the [appendix](/man/manAppendix.html) using the following syntax:

```bash
You can link to a <see href="../man/manAppendix.html#specific-section">specific section</see> of the appendix.
```

* If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of < and >, which is **"\&lt;"** and **"\&gt;"** respectively. This encoding is shown in the following example.



More information about XML comments can be found here:

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/  
https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/recommended-tags  
https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/examples

***

<br>
<br>

# **TAGS**

## \<summary>

* The `<summary>` tag isused by IntelliSense inside Visual Studio to display additional information about a type or member.
* All types must have a `<summary>` tag.

```xml
/// <summary>A short summary of what the class does/is responsible for.</summary>
```

## \<remarks>

* The `<remarks>` tag is used to add information about a type or a type member, supplementing the information specified with `<summary>`.
* Lengthy `<remark>` tags should be separated into `<para>` components.
* This tag may include `<list>` components.

```xml
/// <remarks>
/// <para>
/// The remarks section can...
/// </para>
/// <para>
/// ...be long.
/// </para>
/// </remarks>
```

## \<return>

* The `<return>` tag describes a return value.

```xml
/// <return>Details what is returned.</return>
```

## \<param>

* The `<param>` tag describes a method parameter.

```xml
<param name="name">description</param>
```

## \<value>

* The `<value>` tag describes the value that a property represents.

```xml
<value>TheValue</value>
```

## \<c>

* The `<c>` tag indicates that text within a description should be marked as code.

```xml
<c>Some code</c>
```

## \<code>

* The `<code>` tag indicates multiple lines of code. Use `<c>` to indicate that single-line text within a description should be marked as code.

```xml
<code>
    var index = 5;
    index++;
</code>
```

## \<example>

* The `<example>` tag specifies an example of how to use a method or other library member, and uses the `<code>` tag.

```xml
<example>
This shows how to increment an integer.
<code>
    var index = 5;
    index++;
</code>
</example>
```

***

<br>
<br>

# **FORMATTING**

## \<br/>

* The `<br/>` tag creates a single-spaced paragraph.

```xml
<remarks>
This is an introductory paragraph.
<br/>
This paragraph contains more details.
</remarks>
```

## \<para>

* The `<para>` tag creates a double-spaced paragraph.

```xml
<remarks>
<para>
This is an introductory paragraph.
</para>
<para>
This paragraph contains more details.
</para>
</remarks>
```

## \<list="bullet">

* The `<list="bullet">` tag creates a bulleted list.
* The `<item">` components should be on a single line.

```xml
/// <list type="bullet">
/// <item>The first item</item>
/// <item>The second item</item>
/// </list>
```

## \<list="number">

* The `<list="number">` tag creates a numbered list.
* The `<item">` components should be on a single line.

```xml
/// <list type="number">
/// <item>The first item</item>
/// <item>The second item</item>
/// </list>
```

## \<list="table">

* The `<list="table">` tag creates a table.

```xml
/// <list type="table">
/// <listheader>
/// <term>Setting</term>
/// <description>Description</description>
/// </listheader>
/// <item>
/// <term><b><i>enabled</i></b></term>
/// <description>All Abatab functionality is (potentially) available.</description>
/// </item>
/// <item>
/// <term>disabled</term>
/// <description>Abatab functionality is not available.</description>
/// </item>
/// <item>
/// <term>passthrough</term>
/// <description>All functionality is available, but no changes are made to Avatar.</description>
/// </item>
/// </list>
```

## \<b>

* The `<b>` tag bolds text.
* Used for:
  * Call outs

```xml
<remarks>
This text is <b>bold</b>.
</remarks>
```

## \<i>

* The `<i>` tag itaicizes text.
* Used for:
  * Filenames

```xml
<remarks>
This text is <i>italized</i>.
</remarks>
```

## \<b><i>

* The `<b><i>` tags bolds and italicize text.
* Used for:
  * Default values

```xml
<remarks>
This text is <b><i>bold and italic</b></i>.
</remarks>
```

***

<br>
<br>

# **LINKS**

## \<see cref="member"/>

* The `<see href="member">` tag specifies a reference to a member or field that is available to be called from the current compilation environment.

```xml
<see cref="member"/>
```

## \<see href="url">

* The `<see href="link">` tag specifies a link to a URL from within text.

```xml
You can <see href="url">link</see> to things.</item>
```

## \<see langword="keyword"">

* The `<see href="link">` tag specifies a language keyword.

```xml
<see langword="keyword"/>
```

## \<seealso cref="member"/>

* The `<see href="link">` tag specifies a reference to a member or field that is available to be called from the current compilation environment.

```xml
<seealso cref="member"/>
```

## \<seealso cref="url"/>

* The `<see href="link">` tag specifies a link to a URL.

```xml
You can <seealso href="url">link</seealso> to things.</item>
```

***

<br>
<br>

# **EXAMPLES**

> A class summary w/remarks

* The `<summary>` tag is the only component displayed on the TOC.
* The `<remarks>` tag is the only displayed in the class-specific documentation

```xml
/// <summary>
/// The entry point for Abatab.
/// </summary>
/// <remarks>
/// Abatab receives two things from Avatar:
/// <list type="number">
/// <item>An <see href="../man/manAppendix.html#optionobject">OptionObject</see>, which contains all of the information that Abatab needs to do it's thing</item>
/// <item>A <see href="../man/manAppendix.html#script-paramater">Script Parameter</see> that tells Abatab what it needs to do with the OptionObject.</item>
/// </list>
/// </remarks>
```

> A method with parameters and a bullet list with links.

```xml
/// <summary>
/// Executes script parameter request from Avatar, then returns a potentially modified OptionObject to Avatar.
/// </summary>
/// <param name="sentOptionObject">The original OptionObject sent from Avatar.</param>
/// <param name="scriptParameter">The original Script Parameter request from Avatar.</param>
/// <returns>A finalized OptionObject that will be returned to Avatar.</returns>
/// <remarks>
/// <list type="bullet">
/// <item>This method is required by Avatar.</item>
/// <item>This is the only time a <see href="../man/manAppendix.html#logging">Primeval debug log</see> is written.</item>
/// </list>
/// </remarks>
```

<!-- -->

[Logo]: /.github/resources/img/logo/AbatabLogo-current.png
