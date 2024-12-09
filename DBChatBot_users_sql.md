---
title: DBChatBot Users SQL
description: 
published: false
date: 2024-12-09T20:25:25.454Z
tags: dev
editor: markdown
dateCreated: 2024-12-09T20:25:25.454Z
---

```sql
-- From: https://stackoverflow.com/a/39224859/316700

with users_json (doc) as (
   values
    ('[
        {
          "uuid": "4PC6Af1OlsmRLXl6CagrSr",
          "name": "Front User",
          "email": "front@example.com",
          "crypted_password": "400$8$33$dd51c75548f2aa63$39af0b56825b4e0614597caf279f63e6fa957175e3aef1b7f8ed4e4c39a0524a",
          "password_salt": "1XlNuoI38dl4Wgs1_NRl",
          "perishable_token": "TIfIdpDYPtV4hLl2Ow08",
          "persistence_token": "2a479f1a1f361ec2c986eb0274b0cd503c87847a603011d740a500d2cc3569c6747591d7f4c2eab3fbf76b7023eb51c56b8983b23c53dc3b6b99baa79e7c06ad",
          "created_at": "2024-11-29T14:14:08.371Z",
          "updated_at": "2024-11-29T14:14:08.371Z",
          "notifications_active": [],
          "api_token": "7Et5qwWbzZBIa4tgi5yypp"
        },
        {
          "uuid": "Front User",
          "name": "1KDb3nqBsmeJSytdnbcax1",
          "email": "lucas@theysay.me",
          "crypted_password": "400$8$36$1600576eca8845fc$dfb1dfce4eb382340654d832e1131c4ee604699e7871023c1070cb5251b0acc1",
          "password_salt": "hLlXbzbd5EcM5GFEDQrK",
          "perishable_token": "mLrkBi92G9MeJ0vcgMll",
          "persistence_token": "3e01ad4a3a161e15a190964f132b46e092b0aef05713c90af8fb7520192c9a53e67ab4bfcde23e6e68c83121e01ebdcfaa9b6b3df3ad88005c32caded6469774",
          "created_at": "2024-09-25T19:16:44.000Z",
          "updated_at": "2024-10-01T18:30:51.000Z",
          "notifications_active": [],
          "api_token": "3eM4L1s3GCvkrnpYJqHrgG"
        },
        {
          "uuid": "David",
          "name": "7b2ObXNLalQ4mTZSbGwJ5g",
          "email": "david@theysay.me",
          "crypted_password": "400$8$1f$00176aa398c79569$d6854dad1445b44582a4a9de8c74d08312a123f012ecb7b7e210d75e7c047239",
          "password_salt": "1k3p2FXncQvmxAgUHUkO",
          "perishable_token": "OHUMC4sdCg9r0L_T29a-",
          "persistence_token": "278c02ef67afb12d70b473ce080de6f8d35ee93c9673f173e59eac1d332e4cba8b6403fbb25b4b4d48b74e5187d880ddf2b68baa3d945d5b26c3b56fe1141eee",
          "created_at": "2024-09-23T07:52:58.000Z",
          "updated_at": "2024-10-01T18:30:51.000Z",
          "notifications_active": [],
          "api_token": "17supNUV1Ksgu1slp7Gu3Y"
        },
        {
          "uuid": "Francisco Muñoz",
          "name": "5V9b5ovo08wTajMQKvVmtq",
          "email": "munozbosch@gmail.com",
          "crypted_password": "400$8$29$62655ccd81766ff3$3807aff173ebd08f216734954980add9b7f04a96a00aa8bdada9064598b840fc",
          "password_salt": "chobeoMWvK96B3qzwHLH",
          "perishable_token": "tpjl4dL3d0D6YYzoHXcO",
          "persistence_token": "0567c6d60edb97958a48b43982a0f77d6904791680e97d064a7dade2ba494953a1e69e3c63fbd15b75066997bab7da21f8321e759889e04489971a45780d90ce",
          "created_at": "2024-08-16T21:12:22.000Z",
          "updated_at": "2024-12-05T11:49:41.562Z",
          "notifications_active": [],
          "api_token": "7SGci5LvmqbfpiIeqiwwGF"
        },
        {
          "uuid": "Cesar",
          "name": "1082nGw4ppOezQJsyzeCq9",
          "email": "cesar@orbitacloud.com",
          "crypted_password": "400$8$37$c4f8b610b8bec56f$a5687ea26dd29b31c0ce94cc7962516032b37e9420c5e0cc826b472bb66d2140",
          "password_salt": "MTXg8JdmSTcYoUC2hsa5",
          "perishable_token": "MeOeSjr5PNpKFLOCcC_R",
          "persistence_token": "2193c9be064a1e68a760ea4b6ee5e933c6f260ce51a865f903ea063085f3ed291d1e3f918e9de31fda271b1b6d9a466b38e231810e8e254aac62aebe33701a68",
          "created_at": "2024-10-07T18:24:49.000Z",
          "updated_at": "2024-12-05T20:08:54.363Z",
          "notifications_active": [],
          "api_token": "12oEEofbOe5O4zgUjv8MQi"
        },
        {
          "uuid": "Fernando Guillen",
          "name": "4ivT2IpSj7I8dRDV1uZzXC",
          "email": "fguillen.mail@gmail.com",
          "crypted_password": "400$8$2d$7fa2922b71939b8e$0c7b9633f841b8804783db96ed35f6436770deba58ee38ea99ac2943849e7a21",
          "password_salt": "fu0Hr4HKsLfoCZDum3au",
          "perishable_token": "vprH-Fp0YT72FH-CMiZm",
          "persistence_token": "32c9d09497d7906bef0a31c0ba6de62fdd28e68136f5dd41d1587ec152573a40e669776cb552966c742304d100ec563ef36f68cbfe699fdbe1b19475a965cdf7",
          "created_at": "2024-07-03T21:08:23.000Z",
          "updated_at": "2024-12-06T15:42:28.761Z",
          "notifications_active": [],
          "api_token": "4Vn28wgl2E8Bi1NY7YjhSg"
        }
    ]'::json)
)
insert into front_users (
  uuid,
  name,
  email,
  crypted_password,
  password_salt,
  perishable_token,
  persistence_token,
  created_at,
  updated_at,
  notifications_active,
  api_token
)
select p.*
from users_json l
  cross join lateral json_populate_recordset(null::front_users, doc) as p;

```