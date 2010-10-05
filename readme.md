
<pre style="font-family:courier">
 ___   _           _          _     _ ______                   
|   \ | |         | |        | |   | |____  \                  
| |\ \| | ___   __| |_____   | |___| |____)  )_____  ___ _____ 
| | \   |/ _ \ / _  | ___ |  |  ___  |  __  ((____ |/___) ___ |
| |  \  | |_| ( |_| | ____|  | |   | | |__)  ) ___ |___ | ____|
|_|   |_|\___/ \____|_____)  |_|   |_|______/\_____(___/|_____)
</pre>

Node HBase is a Node.JS client for HBase server. It use the Rest API (Stargate in previous versions) to communicate with HBase. Currently, the data exchange format is json but protocol buffer will follow.

Quick example
-------------

This code create a new HBase instance, create a table and a column family, insert a few records and traverse them.

	var assert = require('assert')
	  , hbase = require('hbase');
	
	hbase({ host: '127.0.0.1', port: 8080 })
	.getTable('node_hbase' )
	.create('node_hbase_column', function(error, success){
		this
		.row('my_row')
		.put('my_column_family:my_column', function(error, success){
			this.get('my_column_family', function(error, cells){
				this.exists(function(error, exists){
					assert.ok(exists);
				}
			}
		});
	});

Installing
----------

Via git (or downloaded tarball):

    $ git clone http://github.com/wdavidw/node-hbase.git

Then, simply copy or link the lib/csv.js file into your $HOME/.node_libraries folder or inside a declared path folder.

Via [npm](http://github.com/isaacs/npm):

    $ npm install hbase

Running the tests
-----------------

Tests are executed with expresso. To install it, simple use `npm install expresso`.

To run the tests
	expresso -I lib test/test*

To develop with the tests watching at your changes
	expresso -w -I lib test/test*

To instrument the tests
	expresso -I lib --cov test/test*



Related projects
----------------

*   Official Apache HBase project: <http://hbase.apache.org/>
*   Brother project Pop HBase (PHP): <http://www.php-pop.org/pop_hbase.html>