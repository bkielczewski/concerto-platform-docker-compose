# Quickstart guide


1. ./concerto/config/parameters.yml - set up db connectivity + secret token for sessions
2. pack this configuration up and deliver to instance (i.e. chef, puppet, rsync)
3. on instance: `docker-compose up -d --build` (or wrap it in systemd unit)
4. consider putting ./shared on NFS volume 
5. should be listening on :80 after a while
