username  =  'username' 
token  =  'token' 
url  =  "https:// #{ username } : #{ token } @api.heroku.com/schema" 
options  =  { 
  default_headers :  { 'Accept'  =>  'application/vnd.heroku+json; version=3' }, 
  cache :  Moneta . new ( :File ,  dir :  " #{ Dir . home } /.heroics/heroku-api" )} 
data  =  JSON . parse ( File . read ( 'schema.json' )) 
schema  =  Heroics :: Schema . new ( data ) 
cli  =  Heroics . cli_from_schema ( 'heroku-api' ,  STDOUT ,  schema ,  url ,  options ) 
cli . run ( * ARGV )
