---
layout: datatables
menu: changelog
---

<h3>Changelog</h3>
<hr />

<h4>0.8.6 (03-05-2013)</h4>

 * Major changes
	*	**New release management** : now, all JARs (core and extras) have the same version number. This will be much clearer and simpler for both developers and users.
	*	**New cache system** : a huge [performance issue](http://github.com/dandelion/issues/issues/34) has been raised by [Julien Dubois](https://github.com/jdubois) during his stress test of the Spring-petclinic app. It has been fixed setting up a basic cache system (a static Map at the moment) that stores the generated web resources (js, css) per request URI and per table DOM id. This way, the DataTables configuration (and other needed assets) are generated only once and then are stored in the [AssetCache](http://github.com/dandelion/dandelion-datatables/blob/master/datatables-core/src/main/java/com/github/dandelion/datatables/core/cache/AssetCache.java). So no need to use the ServletContext any longer, which was decreasing performance.
 * Minor changes
	* Added a new `searchable` / `dt:searchable` attributes (JSP/Thymeleaf) to exclude column from searching
 * Issues
	* [issue #30](https://github.com/dandelion/issues/issues/30) (Export links generation)
	* [issue #32](https://github.com/dandelion/issues/issues/32) (Exclude column from searching)
	* [issue #34](https://github.com/dandelion/issues/issues/34) (Memory leak)
	* [issue #35](https://github.com/dandelion/issues/issues/35) (Wrong use of EVAL_PAGE in the doStartTag method of the ColumnTag)
	* [issue #36](https://github.com/dandelion/issues/issues/36) (Problem with tld file on JBoss 6)

<h4>0.8.5 (02-23-2013)</h4>
<ul>
 <li>Issues
   <ul>
     <li><a href="https://github.com/dandelion/issues/issues/19">issue #19</a> (Shift in the first row if a columnTag has a body)</li>
     <li><a href="https://github.com/dandelion/issues/issues/20">issue #20</a> (ExportLink position issue when Bootstrap2 theme enabled)</li>
   </ul>
 </li>
</ul>

<h4>0.8.4 (02-21-2013)</h4>
<ul>
 <li><strong>DataTables4j</strong> has became <strong>Dandelion-datatables</strong>! See the <a href="migration.html">migration guide</a>!</li>
 <li>Issues
   <ul>
     <li><a href="https://github.com/dandelion/issues/issues/16">issue #16</a> (Dynamic value for table's id)</li>
     <li><a href="https://github.com/dandelion/issues/issues/17">issue #17</a> (Table display issue)</li>
   </ul>
 </li>
</ul>

<hr />

<h4>0.8.3 (02-11-2013)</h4>
<ul>
 <li>Core
   <ul>
     <li>New <code>default</code>/<code>dt:default</code> attributes, allowing you to set default value in case of null values</li>
   </ul>
 </li>
 <li>Modules
  <ul>
   <li>Servlet2 module moved inside the core-parent (for easier distribution) Warning : artifactId has changed to <strong>datatables4j-servlet2</strong></li>
  </ul>
 </li>
 <li>Issues
   <ul>
     <li><a href="https://github.com/datatables4j/issues/issues/24">issue #24</a> (Regression using plugins)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/25">issue #25</a> (scope issue is modules)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/29">issue #29</a> (Sorting issue when using server-side processing)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/31">issue #31</a> (Icons in Bootstrap Theme)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/32">issue #32</a> (Handling null values)</li>
   </ul>
 </li>
</ul>

<h4>0.8.2 (01-31-2013)</h4>
<ul>
 <li>Core
   <ul>
     <li>AJAX sources support, using the <code>url</code>/<code>dt:url</code> attributes</li>
     <li>Server-side processing support and new utility classes !</li>
     <li>New <code>appear</code>/<code>dt:appear</code> attributes, allowing you to choose how the table will appear when he has finished loading</li>
     <li>New <code>serverSide</code>/<code>dt:serverside</code> attributes, that enable server-side processing</li>
     <li>New <code>pipelining</code>/<code>dt:pipelining</code> attributes, to enable data pipelining on paging</li>
     <li>New <code>pipeSize</code>/<code>dt:pipesize</code> attributes, to define the pipe size when pipelining is enabled</li>
     <li>New <code>dt:property</code> Thymeleaf attribute, used with <code>dt:url</code> for AJAX sources</li>
     <li>New <code>dt:labels</code> Thymeleaf attribute, for DataTables i18n support</li>
   </ul>
 </li>
 <li>Modules
  <ul>
   <li>New Spring3 module (at the moment, only used to have a full Spring integration with server-side processing)</li>
   <li>AJAX-Jersey module removed, no need anymore due to AJAX support in datatables4j-core</li>
  </ul>
 </li>
 <li>Issues
   <ul>
     <li><a href="https://github.com/datatables4j/issues/issues/18">issue #18</a> (Wrong MIME type for XLS export)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/17">issue #17</a> (XLS and XLSX exports currently not working)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/10">issue #16</a> (i18n support for the Thymeleaf version)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/11">issue #15</a> (Design issue during DataTables loading)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/11">issue #12</a> (Server-side processing support)</li>
   </ul>
 </li>
</ul>

<h4>0.8.1 (01-20-2013)</h4>
<ul>
 <li>Core
   <ul>
     <li><a href="http://www.thymeleaf.org">Thymeleaf</a> support ! (Even if lots of features still need to be supported...)</li>
     <li>Concept of "theme" added, new <tt>theme</tt> and <tt>themeOption</tt> table attributes</li>
     <li>New themes based on Bootstrap2 and jQuery UI ThemeRoller</li>
     <li>New <tt>display</tt> column attribute : you can now choose which column(s) you want to appear (only in a particular export, only in HTML, or both)</li>
     <li>New <tt>autoSize</tt> export attribute (only for Excel exports)</li>
     <li>Export classes have been updated to handle binary exports (like XLS or PDF)</li>
     <li>Using custom classes for export is now possible</li>
     <li>New values available for <tt>paginationType</tt> table attribute : four_button, bootstrap, scrolling, input, listbox, extJs</li>
     <li><a href="http://code.google.com/p/jquery-datatables-column-filter/">DataTables Column Filter Add-on by Jovan Popovic</a> added (for now, only <tt>filterType</tt> is supported, with INPUT and SELECT values)</li>
     <li>Lots of code duplication removed</li>
   </ul>
 </li>
 <li>Modules
  <ul>
   <li>New Excel (XLS) Export module using Apache POI</li>
   <li>New Excel (XLSX) Export module using Apache POI (OOXML)</li>
   <li>New PDF Export module using iText</li>
  </ul>
 </li>
 <li>Issues
   <ul>
     <li><a href="https://github.com/datatables4j/issues/issues/5">issue #5</a> (Custom header column)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/9">issue #9</a> (Thymeleaf integration)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/10">issue #10</a> (FixedColumns plugin integration)</li>
     <li><a href="https://github.com/datatables4j/issues/issues/11">issue #11</a> (CDN attribute in https context)</li>
   </ul>
 </li>
</ul>

<h4>0.7.0 (11-30-2012)</h4>
<ul>
 <li>Core
   <ul>
     <li>Servlet 3.0 support (Warning : <a href="./install.html">install section</a> has been updated)</li>
     <li>Jackson mapper dependency replaced by Google json-simple one (lighter)</li>
     <li>Basic export functionality (for now CSV and XML are supported) with customizable output filename, export link position, ... See <a href="./features.export.html">more details</a></li>
     <li>New <tt>export</tt> and <tt>exportLinks</tt> table attributes (to enable export and set one or several links positions)</li>
     <li>New Export tag (to configure one export\'s type)</li>
     <li>Javascript and JSON configuration are now pretty printed (as much as possible :-))</li>
     <li>More documentation (Javadoc et web site)</li>
     <li>DataTables4j now released under the BSD 3-Clause licence</li>
   </ul>
 </li>
 <li>Modules
  <ul>
   <li>New backward compatibility module for Servlet 2.x</li>
   <li>YUI Compression module : compression option (munge, preserve semi-colons, disable optimizations) are now externalized in the DataTables4j properties file</li>
  </ul>
 </li>
 <li>Demo apps
  <ul>
   <li>The main demo is now deployed in a Tomcat 7 container (Servlet 3.0)</li>
   <li>New <strong>Features > Export</strong> examples</li>
   <li><strong>Features > Aggregation</strong> section updated</li>
   <li>New demo using the backward compatibility module for Servlet 2.x deployed to CloudBees</li>
  </ul>
 </li>
 <li>Bug
   <ul>
     <li>Fix for <a href="https://github.com/datatables4j/issues/issues/1">issue #1</a> (The prop tag affects all tables, not just the current one)</li>
     <li>Fix for <a href="https://github.com/datatables4j/issues/issues/3">issue #3</a> (EL in title attribute of the column tag)</li>
   </ul>
 </li>
</ul>

<h4>0.6.0 (11-10-2012)</h4>
<ul>
 <li>Core
   <ul>
     <li>Creation of a wrapper for API and implementation "datatable4j-core", for maven users</li>
     <li>Creation of a standalone version of this wrapper "datatable4j-core-*-standalone.jar", for other users</li>
     <li>Main servlet uses Servlet 3.0, changing prerequisites. See <a href="./install.html">install</a> for more details.</li>
     <li>Now in Maven Central !</li>
   </ul>
 </li>
</ul>

<h4>0.5.0-SNAPSHOT (10-07-2012)</h4>

<ul>
 <li>Core
  <ul>
   <li>Concept of "feature" (e.g. filtering) and FeatureLoader added</li>
   <li>New column filtering attributes <code>filterType</code>, <code>filterCssClass</code> and <code>filterPlaceholder</code></li>
   <li>New column sorting attributes <code>sortInit</code> and <code>sortDirection</code></li>
   <li>New table attribute <code>jqueryUI</code></li>
   <li>Properties loading improved (allowing to remove slf4j dependency from core-api)</li>
   <li>Random number is now unique per table (if several files need to be generated for a table)</li>
   <li>Generalization of the initialization-on-demand holder strategy for singletons</li>
   <li>Packages and classes reorganization, this is much clearer ! (Warning : the main servlet is now in org.datatables4j.core.web.servlet.*, not in org.datatables4j.web.servlet.* anymore)</li>
   <li>License notices attached to the start of eeeeaach file ...</li>
  </ul> 
 </li>
 <li>Demo application
  <ul>
   <li>New example for <code>filterType</code>, <code>filterCssClass</code> and <code>filterPlaceholder</code> attributes (see <a href="${demoAppUrl}basic/filtering" target="_BLANK">here</a>)</li> 
   <li>New example for <code>sortInit</code> and <code>sortDirection</code> attributes (see <a href="${demoAppUrl}basic/sorting" target="_BLANK">here</a>)</li>
  </ul>
 </li>
</ul>

<h4>0.4.0-SNAPSHOT (10-02-2012)</h4>

<ul>
 <li>Core
  <ul>
   <li>i18n support via <code>labels</code> attribute</li>
   <li><code>lengthChange</code> added</li>
   <li>Jersey and YUICompressor dependencies removed and externalized in modules</li>
   <li>commons-io dependency removed</li>
   <li>Code cleaning</li>
   <li>Comments added</li>
  </ul> 
 </li>
 <li>Demo application
  <ul>
   <li>New example for i18n support</li>
   <li>New example for plugins combo and aggregation added</li>
  </ul>
 </li>
</ul>

<h4>0.3.0-SNAPSHOT (09-27-2012)</h4>

<ul>
 <li>Core
  <ul>
   <li>Code cleaning</li>
  </ul> 
 </li>
 <li>Demo application
  <ul>
   <li>Doc tag added to generate documentation links</li>
   <li>All JSP updated with new taglib URI</li>
   <li>Added plugins and features section</li>
  </ul>
 </li>
</ul>

<h4>0.2.0-SNAPSHOT (09-25-2012)</h4>

<ul>
 <li>Core
  <ul>
   <li>New TLD URI</li>
   <li>Servlet API version downgraded to 2.5</li>
   <li>Fix for properties file loading</li>  
  </ul>
 </li>
 <li>Demo application
  <ul>
   <li>TLD URI updated</li>
   <li>Added DataTables4j servlet definition</li>
  </ul>
 </li>
</ul>

<h4>0.1.0-SNAPSHOT (09-24-2012)</h4>

<ul>
<li>Code refactoring</li>
<li>Lots of comments added</li>
<li>New attribute <code>offsetTop</code> for fixedHeader module</li>
<li>URL cleaning for files served by the Datatables4jServlet</li>
<li>POM update for new snapshot and Cloudbees integration</li>
<li>Demo application deployed on Cloudbees !</li>
</ul>

<h4>0.0.0-SNAPSHOT (09-10-2012)</h4>

<ul>
<li>Project initialisation</li>
</ul>