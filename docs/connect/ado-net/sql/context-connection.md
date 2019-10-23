---
title: Connexion de contexte
description: Décrit la connexion de contexte.
ms.date: 08/15/2019
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: b5ebd0b1b7357a385507d1ab528adde4023092da
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452263"
---
# <a name="the-context-connection"></a>Connexion de contexte

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Le problème d'accès aux données interne est un scénario relativement courant. Autrement dit, vous souhaitez accéder au même serveur que celui sur lequel votre fonction ou procédure stockée CLR s'exécute. Une option consiste à créer une connexion à l'aide de <xref:Microsoft.Data.SqlClient.SqlConnection>, en spécifiant une chaîne de connexion qui pointe sur le serveur local, et à ouvrir la connexion. Cela requiert la spécification d'informations d'identification pour se connecter. La connexion se trouve dans une autre session de base de données que la procédure stockée ou la fonction, elle peut avoir des options `SET` différentes, elle figure dans une transaction distincte, elle ne consulte pas vos tables temporaires, et ainsi de suite Si le code de votre procédure stockée managée ou de votre fonction exécute dans le processus SQL Server, la raison en est que quelqu'un s'est connecté à ce serveur et a exécuté une instruction SQL pour l'appeler. Vous souhaitez probablement que la procédure stockée ou la fonction s'exécute dans le contexte de cette connexion, avec sa transaction, ses options `SET`, et ainsi de suite. Une telle connexion est appelée connexion du contexte, ou connexion contextuelle.  
  
La connexion contextuelle permet d'exécuter des instructions Transact-SQL dans le même contexte que celui où votre code a été appelé en premier lieu. Pour plus d’informations, consultez [la connexion contextuelle](https://go.microsoft.com/fwlink/?LinkId=115395) à partir de documentation en ligne de SQL Server.
