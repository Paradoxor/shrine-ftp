# shrine-ftp
Shrine storage that handles file uploads to an FTP server

## Usage
Refer to the Shrine [Quick start](http://shrinerb.com/rdoc/files/README_md.html#label-Quick+start) if you need to
know how to set up storage in the first place.

```
require "shrine"
require "shrine/storage/file_system"
# require ftp storage type
require "shrine/storage/ftp" 

storage = Shrine::Storage::Ftp.new(
    host: 'ftp.yourhost.com',
    user: 'ftp_user',
    password: 'ftp_password',
    dir: 'projectx',
    prefix: 'https://poly-amorie.com'
)
# https://poly-amorie.com/projectx/users/d1ba5412-0ba3-4a1d-a8ae-1ed7d765085f/verifyimage/1875822c36d6b0c52639f230bf5bf75b.jpeg

Shrine.storages = {
    cache: Shrine::Storage::FileSystem.new('public', prefix: 'uploads/cache'),
    store: storage
}
```