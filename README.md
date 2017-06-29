var Twitter = require('twitter');
 
var client = new Twitter({
  consumer_key: "wN6JJFywXFt80pFIrJhWnIVz3",
  consumer_secret: "Om3gtRF6vshz7OWV5BWvPJka3GwvtrbFyXNBANmKvO2Zfqnphv",
  access_token_key: 	"763861624130240512-HEJZoN6PddWGZd1hlPNjD18tfsmuHsx",
  access_token_secret: "vYoBqPM0WSBpAcKgCxJkbQZaKfuuwffG1o6Wab0nVGenE"
});
 
var params = {screen_name: 'nodejs'};
client.get('statuses/user_timeline', params, function(error, tweets, response) {
  if (!error) {
    console.log(tweets);
  }
});

var stream = client.stream('statuses/filter', {track: 'javascript'});
stream.on('data', function(event) {
  console.log(event && event.text);
});
 
stream.on('error', function(error) {
  throw error;
});
 
// You can also get the stream in a callback if you prefer. 
client.stream('statuses/filter', {track: 'javascript'}, function(stream) {
  stream.on('data', function(event) {
    console.log(event && event.text);
  });
 
  stream.on('error', function(error) {
    throw error;
  });
});
