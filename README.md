# OpenAPI Go SDK

Данный проект представляет собой инструментарий на языке Go для работы с OpenAPI Тинькофф Инвестиции, который можно использовать для создания торговых роботов.

## Начало работы

### Где взять токен аутентификации?

В разделе инвестиций вашего  [личного кабинета tinkoff](https://www.tinkoff.ru/invest/) . Далее:

* Перейдите в настройки
* Проверьте, что функция “Подтверждение сделок кодом” отключена
* Выпустите токен для торговли на бирже и режима “песочницы” (sandbox)
* Скопируйте токен и сохраните, токен отображается только один раз, просмотреть его позже не получится, тем не менее вы можете выпускать неограниченное количество токенов

## Документация

Документацию непосредственно по OpenAPI можно найти по [ссылке](https://api-invest.tinkoff.ru/openapi/docs/).

### Быстрый старт

Для непосредственного взаимодействия с OpenAPI нужно создать клиента. Клиенты разделены на streaming market data и rest trading

```go
package main

import (
	"log"
	"os"

	sdk "stash.tcsbank.ru/g.kirilenko/invest-openapi-go-sdk"
)

func main() {
	const token = "your_token"

	logger := log.New(os.Stdout, "", log.LstdFlags)

	streamClient, err := sdk.NewMarketClient(logger, token)
	if err != nil {
		logger.Fatalln(err)
	}

	restClient := sdk.NewTradingClient(token)
}
```

### У меня есть вопрос

[Основной репозиторий с документацией](https://github.com/TinkoffCreditSystems/invest-openapi/) — в нем вы можете задать вопрос в Issues и получать информацию о релизах в Releases.
Если возникают вопросы по данному SDK, нашёлся баг или есть предложения по улучшению, то можно задать его в Issues, либо писать на почту:
* Мельникову Никите ( [n.v.melnikov@tinkoff.ru](mailto:n.v.melnikov@tinkoff.ru) )
* Кириленко Георгию ( [g.kirilenko@tinkoff.ru](mailto:g.kirilenko@tinkoff.ru) )
