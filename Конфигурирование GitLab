nginx['custom_gitlab_server_config'] = "location ~/artifacts/file/.*\.(html|txt|md|css|js|jpg|jpeg|png|json)$ {
rewrite ^(.*)/file/(.*)$ $1/raw/$2 last;
return 500;
}
location ~ /artifacts/raw/.*\.(md|css|js|jpg|jpeg|png|json)$ {
proxy_cache off;
proxy_pass http://gitlab-workhorse;
proxy_hide_header Content-Disposition;
add_header Content-Disposition 'inline;';
proxy_hide_header Content-Type;
proxy_hide_header X-Content-Type-Options;
}
location ~ /artifacts/raw/.*\.(html|txt)$ {
proxy_cache off;
proxy_pass http://gitlab-workhorse;
proxy_hide_header Content-Disposition;
add_header Content-Disposition 'inline;';
proxy_hide_header Content-Type;
add_header Content-Type 'text/html; charset=utf-8';
}"
