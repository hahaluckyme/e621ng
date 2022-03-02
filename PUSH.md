# how to push
```sh
git pull
RAILS_ENV=production rake assets:precompile
# stop server
foreman start
```

# how to backup
```sh
now=$(date +"%Y-%m-%d")
/usr/bin/pg_dump -F t danbooru2 > /home/danbooru/backup_psql/danbooru2_$now.tar
/usr/bin/tar -czf /home/danbooru/backup_psql/data_$now.tar.gz /home/danbooru/backup
```

# how to restore
```sh
pg_restore -c -d danbooru2 danbooru2_2021-11-26.tar
bin/rails r Post.import!
# todo: unpack data folder tar.gz
```

