Luvit port of node-mysql
===
<a href="http://travis-ci.org/kengonakajima/luvit-mysql"><img src="https://secure.travis-ci.org/kengonakajima/luvit-mysql.png"></a>

Luvit port of [node-mysql](https://github.com/felixge/node-mysql) .

Much code is from node-mysql JavaScript source. Thank for former work!


Example
====

<pre>
local MySQL = require("mysql")

local db = MySQL({
	database = "leveling",
	user = "leveling",
	password = "himom",
	port = 3306,
})

db:Query("CREATE TABLE IF NOT EXISTS `leveling` (`id` BIGINT UNSIGNED NOT NULL, `rating` BIGINT UNSIGNED NOT NULL, `exp` BIGINT UNSIGNED NOT NULL, PRIMARY KEY (`userid`));")

local exp = db:QueryValue("SELECT `exp` FROM `leveling` WHERE `id` = ?;", "299355776655556608", "exp")
local row = db:QueryRow("SELECT `exp`, `id` FROM `leveling` WHERE `id` = ?;", "299355776655556608")
local leaders = db:Query("SELECT * FROM `leveling` ORDER BY `exp` DESC LIMIT ? OFFSET ?;", {5, 10})
</pre>