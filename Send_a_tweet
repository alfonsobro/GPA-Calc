#How to send a tweet

require 'rubygems'
require 'oauth'
require 'json'

consumer_key = OAuth::Consumer.new(
    "*insert Consumer key*")
access_token = OAuth::Token.new(
    "* insert access token*")
    
    
baseurl = "https://api.twitter.com"
path    = "/1.1/statuses/update.json"
address = URI("#{baseurl}#{path}")
request = Net::HTTP::Post.new address.request_uri
request.set_form_data(
"status" => "Testing",
   )
   


http             = Net::HTTP.new address.host, address.port
http.use_ssl     = true
http.verify_mode = OpenSSL::SSL::VERIFY_PEER

request.oauth! http, consumer_key, access_token
http.start
response = http.request request

tweet = nil
if response.code == '200' then
  tweet = JSON.parse(response.body)
  puts "Successfully sent #{tweet["text"]}"
else
  puts "Could not send the Tweet! " +
  "Code:#{response.code} Body:#{response.body}"
end
