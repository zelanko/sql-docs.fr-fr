---
title: Connexion de contexte | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f6334964a58e643ad373aa8fb0599f39bd3ba01c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919232"
---
# <a name="context-connection"></a>Connexion contextuelle
  Le problème d'accès aux données interne est un scénario relativement courant. Autrement dit, vous souhaitez accéder au même serveur que celui sur lequel votre fonction ou procédure stockée CLR s'exécute. Une option consiste à créer une connexion à l'aide de `System.Data.SqlClient.SqlConnection`, en spécifiant une chaîne de connexion qui pointe sur le serveur local, et à ouvrir la connexion. Cela requiert la spécification d'informations d'identification pour se connecter. La connexion se trouve dans une autre session de base de données que la procédure stockée ou la fonction, elle peut avoir des options `SET` différentes, elle figure dans une transaction distincte, elle ne consulte pas vos tables temporaires, et ainsi de suite Si le code de votre procédure stockée managée ou de votre fonction exécute dans le processus SQL Server, la raison en est que quelqu'un s'est connecté à ce serveur et a exécuté une instruction SQL pour l'appeler. Vous souhaitez probablement que la procédure stockée ou la fonction s'exécute dans le contexte de cette connexion, avec sa transaction, ses options `SET`, et ainsi de suite. Une telle connexion est appelée connexion du contexte, ou connexion contextuelle.  
  
 La connexion contextuelle permet d'exécuter des instructions Transact-SQL dans le même contexte que celui où votre code a été appelé en premier lieu. Pour obtenir la connexion contextuelle, vous devez utiliser le mot clé "context connection" de la chaîne de connexion, comme dans l'exemple ci-après :  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Connexions normales et contextuelles](context-connections-vs-regular-connections.md)  
 Décrit les différences entre les connexions régulières et les connexions contextuelles.  
  
 [Restrictions applicables aux connexions normales et contextuelles](context-connections-and-regular-connections-restrictions.md)  
 Décrit les restrictions sur les connexions régulières et les connexions contextuelles.  
  
  
