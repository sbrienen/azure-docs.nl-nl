---
author: yegu-ms
ms.service: redis-cache
ms.topic: include
ms.date: 11/09/2018
ms.author: yegu
ms.openlocfilehash: 61e93e3700b9a396d2ac4fdcbb51fc5c874cf9cb
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/02/2020
ms.locfileid: "68286153"
---
.NET-toepassingen kunnen de cache-client **StackExchange.Redis** gebruiken. Deze kan in Visual Studio worden geconfigureerd met een NuGet-pakket dat de configuratie van de cacheclienttoepassingen eenvoudiger maakt. 

> [!NOTE]
> Zie de [stack Exchange. redis](https://github.com/StackExchange/StackExchange.Redis) github-pagina en de [stack Exchange. Azure-cache voor redis-client documentatie](https://github.com/StackExchange/StackExchange.Redis#documentation)voor meer informatie.
>
>

Als u in Visual Studio een clienttoepassing wilt configureren met het NuGet-pakket StackExchange.Redis, klikt u in **Solution Explorer** met de rechtermuisknop op het project en kiest u **Manage NuGet Packages**. 

![Manage NuGet Packages](media/redis-cache-configure-stackexchange-redis-nuget/redis-cache-manage-nuget-menu.png)

Typ in het zoekvak **StackExchange.Redis** of **StackExchange.Redis.StrongName**, selecteer de gewenste versie in de resultaten en klik op **Install**.

> [!NOTE]
> Als u liever een versie van de clientbibliotheek **StackExchange.Redis** gebruikt met een sterke naam, kiest u **StackExchange.Redis.StrongName**. Kies anders **StackExchange.Redis**.
>
>

![NuGet-pakket StackExchange.Redis](media/redis-cache-configure-stackexchange-redis-nuget/redis-cache-stackexchange-redis.png)

Met het NuGet-pakket downloadt u de vereiste assembly-verwijzingen voor de clienttoepassing en voegt u deze toe om met de StackExchange.Azure Cache voor Redis-client toegang te krijgen tot Azure Cache voor Redis.

> [!NOTE]
> Als u uw project eerder hebt geconfigureerd voor gebruik van StackExchange.Redis, kunt u bij **NuGet Package Manager** controleren op updates voor het pakket. Als u de bijgewerkte versies van het NuGet-pakket stack Exchange. redis wilt controleren en installeren, klikt u op **updates** in het venster **NuGet package manager** . Als er een update voor het StackExchange.Redis-pakket NuGet beschikbaar is, kunt u uw project bijwerken zodat de bijgewerkte versie wordt gebruikt.
>
>

U kunt het StackExchange.Redis-pakket NuGet ook installeren door in het menu **Hulpprogramma's** te klikken op **NuGet Package Manager**, **Package Manager Console** en in het venster **Package Manager Console** de volgende opdracht uit te voeren.

```
Install-Package StackExchange.Redis
```
