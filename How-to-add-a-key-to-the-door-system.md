1. ssh admin@10.10.3.15 (password in hackerpass)
1. sudo su
1. journalctl -ef

Now scan the new card, the system will not recognize it, and will enter the id hash of the unknown card in the log.

1. copy the id of the card
1. (this part needs a user with staff access) log into https://hackeriet.no/hula/admin/auth/user/
1. select correct user from the list
1. enter the id in the `RFID access card number. (new):` field (and maybe the `RFID access card secret code (old):` one too, just to be sure)
