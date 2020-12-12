install:<br>
<code>npm i node-fetch</code><br>
in <code>config.js</code><br>
insert this code:<br>
<code> exports.dokan = {
    endpoint: 'https://www.test.com/wp-json/',
    header: {
        method: 'get',
        headers: { 'Cache-Control': 'no-cache', 'Authorization': 'Bearer INSERT_YOUR_TOKEN_HERE' },
    }
}</code><br>

for routes file <code>test.js</code><br>
insert:<br>
<code> <br>
var fetch = require('node-fetch');<br>
exports.getAllStores = function(callback) {
    fetch(config.dokan.endpoint + 'dokan/v1/stores/3', config.dokan.header)
        .then(res => res.json())
        .then(json => {
            callback(json);
        });
}
</code><br>
in <code>test.js</code> you can change <b>dokan/v1/stores/3</b> with your custom API from https://wedevsofficial.github.io/dokan/ <br><br>
in <code> index.js</code><br> 

<code>
var test = require('./test');
router.get('YOUR_TRIGGER_URL', function(req, res, next) {
    test.getAllStores(function(result) {
        res.send(result);
    });
});
</code>

