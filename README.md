# First init

Launch the docker stack
>  docker-compose up -d

Init lnd and choose your password
> docker-compose exec lnd lncli create

Edit **./data/lnd/lnd.password** file and replace <MyPassWord> string

Restart lnd
> docker-compose restart lnd

Get the watchtower address
```
$ *docker-compose exec lnd lncli tower info*
{
    "pubkey": "0368d7d26b2a48daecf57148c66520a94d93435dd33066af5776b9d80883dfe782",
    "listeners": [
        "[::]:9911"
    ],
    "uris": [
        "0368d7d26b2a48daecf57148c66520a94d93435dd33066af5776b9d80883dfe782@w6fsnxcemcybsllra7snxcmqrzsvzfvo66iciifqix5wnamcq3znd5yd.onion:9911"
    ]
}
```

# Use the watchtower
Add the watchtower to your lnd node (replace <uris> by YOUR watchtower uris)

> lncli wtclient add <uris>


Verify that the watchtower client is using your watchtower (replace <pubkey> by YOUR watchtower public key)
> lncli wtclient tower <pubkey> 
