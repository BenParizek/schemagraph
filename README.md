<h1>SchemaGraph: Visualizing Complex Databases</h1>

<p><a href="http://westonruter.github.com/schemagraph/example.svg" title="View example SVG image generated by SchemaGraph"><img src="http://westonruter.github.com/schemagraph/example.png" alt="Graph visualization of a MySQL database with the tables placed around a circle and the foreign key constraints appearing as lines between the tables" /></p>

<p><dfn>SchemaGraph</dfn> is a MySQL database schema visualization tool inspired by <a href="http://mkweb.bcgsc.ca/schemaball/">Schemaball</a>. Recently I've been working on a <a href="http://openscriptures.org/" title="Open Scriptures">personal project</a> that has a complex schema structure; it has many tables and dozens of foreign key constraints among them. I need a tool which displays all of the tables at once and all of the interrelationships among them so that I can keep track of what is going on. I would have used Schemaball instead of developing a new solution, but I found a couple disadvantages with Schemaball: it generates static raster images when I wanted a dynamic vector images, and its requirements include several dependencies on Perl modules which can be a hassle to install. I really liked the format that Schemaball used to visualize a database schema, but I just wanted to have a standalone script which I could place on a web server, point it at a database, and have it generate an interactive SVG image. To use with future projects, I wanted maximum portability and minimal configuration with immediate results.</p>

<p>SchemaGraph, like Schemaball, queries the MySQL <code>information_schema</code> database to get all of the necessary information about a database's (InnoDB) tables to construct a graph; this graph is then output as an interactive <a href="http://en.wikipedia.org/wiki/Scalable_Vector_Graphics" title="Scalable Vector Graphics">SVG</a> image (see <a href="http://westonruter.github.com/schemagraph/example.svg">example</a>) with the following features:</p>

<ul>
	<li>Tables in the schema are placed equidistantly around a circle.</li>
	<li>Clicking the image causes the graph to rotate.</li>
	<li>Foreign key constraints are represented by bézier curves connecting table labels.</li>
	<li>Hovering over a table or a constraint causes the table's label to highlight along with all of its constraint paths (both incoming and outgoing).</li>
	<li>The paths representing incoming foreign key constraints are highlighted in a different color than outgoing constraints.</li>
	<li>Multiple constraints between the same two tables are prevented from overlapping by giving a unique curve to each of the lines.</li>
	<li>Hovering over a constraint produces a tooltip which shows the names of the fields that are linked by the constraint.</li>
</ul>

<p>To use this tool, simply place <a href="http://github.com/westonruter/schemagraph/blob/master/schemagraph.php">schemagraph.php</a> on a web server and provide values for the constants needed to establish the database connection. You may also modify the constants for the circle radius, font size, and image dimensions. Since the script outputs plain SVG with inline CSS and JavaScript, you may further customize it as needed to get the desired style or behavior.</p>

<p>The code is released under the <a href="http://creativecommons.org/licenses/GPL/2.0/">GNU General Public License 2.0</a>.</p>

<p>(I have put redirects from my blog to GitHub, so the comments on my blog are no longer accessible there. For archive purposes, I've posted the <a href="http://westonruter.github.com/schemagraph/wordpress-comment-archive.html">raw comments</a> to gh-pages.)</p>
