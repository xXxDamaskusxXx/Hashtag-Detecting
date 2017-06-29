var Twitter = require('twitter');

var client = new Twitter({
  consumer_key: "wN6JJFywXFt80pFIrJhWnIVz3",
  consumer_secret: "Om3gtRF6vshz7OWV5BWvPJka3GwvtrbFyXNBANmKvO2Zfqnphv",
  access_token_key: 	"763861624130240512-HEJZoN6PddWGZd1hlPNjD18tfsmuHsx",
  access_token_secret: "vYoBqPM0WSBpAcKgCxJkbQZaKfuuwffG1o6Wab0nVGenE"
});
 
 
 /*
var params = {screen_name: 'nodejs'};
var a = 0
client.get('statuses/user_timeline', params, function(error, tweets, response) {
  if (!error && a === 0) {
    console.log(tweets);
	a = 1
  }
});
*/


var stream = client.stream('statuses/filter', {track: 'javascript'});

stream.on('data', function(tweet) {
  console.log(tweet.text);
  console.log(tweet.user.name);
  console.log(tweet.entities.hashtags)
  
});
 
stream.on('error', function(error) {
  throw error;
});
 
