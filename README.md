require 'faraday'
require 'faraday/retry'

retry_options = {
  max: 2,
  interval: 0.05,
  interval_randomness: 0.5,
  backoff_factor: 2
}

conn = Faraday.new(...) do |f|
  f.request :retry, retry_options
  #...
end

conn.get('/')
