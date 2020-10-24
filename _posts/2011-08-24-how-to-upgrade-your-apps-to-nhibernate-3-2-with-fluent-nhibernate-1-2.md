---
title: "How to upgrade your apps to NHibernate 3.2 with Fluent NHibernate 1.2"
date: 2011-08-24 21:24
category: 
author: 
tags: [fluent nhibernate, nhibernate, upgrade]
summary: 
---

Since version 3.0 the number of files that NHibernate uses shrink. So first, you need to know what kind of files you need to update and delete.

In version 3.0 NHibernate:
<ul>
 	<li>
<ul>
 	<li>NHibernate</li>
 	<li>Iesi.Collections</li>
 	<li>Remotion.Data.Linq</li>
 	<li>NHibernate.ByteCode.Castle</li>
 	<li>Castle.Core</li>
 	<li>Antlr.Runtime</li>
</ul>
</li>
</ul>
In version 3.1, Antlr.Runtime and Remotion.Data.Linq have been ILMerged into NHibernate
<ul>
 	<li>NHibernate</li>
 	<li>Iesi.Collections</li>
 	<li>NHibernate.ByteCode.Castle</li>
 	<li>Castle.Core</li>
</ul>
<span style="color: #666666">In version 3.2,&nbsp; NHibernate integrates a default lazy provider based on LinFu</span>
<ul>
 	<li>NHibernate</li>
 	<li>Iesi.Collections</li>
</ul>
<span style="color: #666666">To upgrade to the last version 3.2 you need to update the last two DLLs and delete the rest ( </span><span style="color: #555555"><a href="http://sourceforge.net/projects/nhibernate/files/NHibernate/3.2.0GA/NHibernate-3.2.0.GA-bin.zip/download">here</a> ).</span>

<span style="color: #555555">If your app uses any DLLs from <a href="http://sourceforge.net/projects/nhcontrib/files/">NHibernate Contrib</a> you need to update them to the version 3.2. </span>

Next you need to download Fluent NHibernate 1.2 ( <a href="http://fluentnhibernate.org/downloads/releases/fluentnhibernate-NH3.1-1.2.zip">here</a> ).

After the update of Fluent DLLs is necessary to change the fluent configuration, to start using the default lazy proxy.

From:
<pre class="brush: csharp; ruler: true;">.ExposeConfiguration(c =&gt; c.SetProperty( Environment.ProxyFactoryFactoryClass, typeof( ProxyFactoryFactory ).AssemblyQualifiedName))</pre>
&nbsp;

To:
<pre class="brush: csharp; ruler: true;">.ExposeConfiguration(c =&gt; c.SetProperty( Environment.ProxyFactoryFactoryClass, typeof( DefaultProxyFactoryFactory ).AssemblyQualifiedName))</pre>
&nbsp;

And because Fluent 1.2 expects NHibernate 3.1 you need to redirect the DLL in .config.
<pre class="brush: xml; ruler: true;">&lt;runtime&gt;
   &lt;assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"&gt;
       &lt;dependentAssembly&gt;
          &lt;assemblyIdentity name="NHibernate" publicKeyToken="aa95f207798dfdb4" culture="neutral" /&gt;
          &lt;bindingRedirect oldVersion="0.0.0.0-3.2.0.4000" newVersion="3.2.0.4000"/&gt;
       &lt;/dependentAssembly&gt;
    &lt;/assemblyBinding&gt;
&lt;/runtime&gt;</pre>
&nbsp;

<span style="font-family: georgia">Is possible to avoid the redirect, if you download the source code of Fluent NHibernate 1.2 and create a build with NHibernate 3.2 DLLs.</span>

<!--EndFragment-->