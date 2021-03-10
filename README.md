# nodejs-test

Test task for Node jS developers. Candidate should write a simple NPM package banking application in Typescript language.

### General acceptance criteria

- All code is in `git` repo (candidate can use his/her own github account).
- Package name can be derived from `ExBanking`
- Package simply exports just an initializer of the `ExBanking` module (no API endpoint, no REST / SOAP API, no TCP / UDP sockets, no any external network interface).
- Application should `not` use any database / disc storage. All needed data should be stored only in application memory.
- Candidate can use any Node library he/she wants to, the code itself should be written using Typescript and transpiled to Javascript.
- We expect unit tests.
- Code accuracy also matters. Readable, safe, refactorable code is a plus.

### Money amounts

- Money amount of any currency should `not` be negative.
- Application should provide `2 decimal` precision of money amount for any currency.
- Amount of money incoming to the system should be equal to amount of money inside the system + amount of withdraws (money should not appear or disappear accidentally).
- User and currency type is any string. Case sensitive. New currencies / users can be added dynamically in runtime. In the application, there should be a special public function (described below) for creating users. Currencies should be created automatically (if needed).

### API reference

Requirements for public functions provided by `ExBanking` package. Any function should return success result or error result. Success result is different for each function, error result is generic

```
type BankingError = Error | 
  WrongArguments | 
  UserAlreadyExists | 
  UserDoesNotExist |
  NotEnoughMoney | 
  SenderDoesNotExist | 
  ReceiverDoesNotExist;
```

```
type Ok = { success: true };
```

`const createUser = (username: string): Ok | BankingError => {};`

- Function creates new user in the system
- New user has zero balance of any currency

`const deposit = (username: string, amount: number, currency: string): (Ok & { newBalance: number } | BankingError) => {};`

- Increases user's balance in given `currency` by `amount` value
- Returns `newBalance` of the user in given format

`const withdraw = (username: string, amount: number, currency: string): (Ok & { newBalance: number } | BankingError) => {};`

- Decreases user's balance in given `currency` by `amount` value
- Returns `new_balance` of the user in given format

`const getBalance = (username: string, currency: string): (Ok & { balance: number } | BankingError) => {};`

- Returns `balance` of the user in given format

`const send = (fromUsername: string, toUsername: string, amount: number, currency: string): (Ok & { fromUsernameBalance: number, toUsernameBalance: number } | BankingError) => {};`

- Decreases `fromUsername`'s balance in given `currency` by `amount` value
- Increases `toUsername`'s balance in given `currency` by `amount` value
- Returns `balance` of `fromUser` and `toUser` in given format

### Notes

- Completed Node JS test tasks can be sent to **HR@heathmont.net**

<!-- Global site tag (gtag.js) - Google Analytics -->
<script async="async" src="https://www.googletagmanager.com/gtag/js?id=UA-109361792-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-109361792-1');
</script>
