# net-sftp-ssh_signature_type

This is a monkey patch to fix the ruby net/sftp error: "undefined method `ssh_signature_type' for #<OpenSSL::PKey::EC::Point"

```
# Warning MONKEY PATCH for "undefined method `ssh_signature_type'"
if ! OpenSSL::PKey::EC::Point.instance_methods(true).include? :ssh_signature_type
  class OpenSSL::PKey::EC::Point
    def ssh_signature_type
      ssh_type
    end
  end
end
```
