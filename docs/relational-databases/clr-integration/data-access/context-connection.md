---
title: Connexion contextuelle | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
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
ms.openlocfilehash: 3b091f515af926fb17cea424b4f8875baf0fa83a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068420"
---
# <a name="context-connection"></a>Connexion contextuelle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le problème d'accès aux données interne est un scénario relativement courant. Autrement dit, vous souhaitez accéder au même serveur que celui sur lequel votre fonction ou procédure stockée CLR s'exécute. Une option consiste à créer une connexion à l’aide de **System. Data. SqlClient. SqlConnection**, à spécifier une chaîne de connexion qui pointe vers le serveur local et à ouvrir la connexion. Cela requiert la spécification d'informations d'identification pour se connecter. La connexion se trouve dans une session de base de données différente de la procédure stockée ou de la fonction, elle peut avoir des options **Set** différentes, elle se trouve dans une transaction distincte, elle ne voit pas vos tables temporaires, et ainsi de suite. Si le code de votre procédure stockée managée ou de votre fonction exécute dans le processus SQL Server, la raison en est que quelqu'un s'est connecté à ce serveur et a exécuté une instruction SQL pour l'appeler. Vous souhaitez probablement que la fonction ou la procédure stockée s’exécute dans le contexte de cette connexion, avec sa transaction, les options **Set** , etc. Une telle connexion est appelée connexion du contexte, ou connexion contextuelle.  
  
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
 [Connexions normales et connexions contextuelles](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 Décrit les différences entre les connexions régulières et les connexions contextuelles.  
  
 [Restrictions applicables aux connexions normales et contextuelles](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 Décrit les restrictions sur les connexions régulières et les connexions contextuelles.  
  
  
