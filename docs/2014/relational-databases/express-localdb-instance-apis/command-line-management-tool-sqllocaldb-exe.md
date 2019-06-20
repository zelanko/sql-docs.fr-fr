---
title: 'Outil de gestion en ligne de commande : SqlLocalDB.exe | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 58ea983555fdcb4bb177813db88d40f4bcc59c0e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128783"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Outil de gestion en ligne de commande : SqlLocalDB.exe
  SqlLocalDB.exe est un outil simple qui permet à l'utilisateur de gérer facilement les instances de LocalDB à partir de l'invite de commandes. Il est implémenté comme wrapper simple autour de l'API de l'instance de LocalDB. Comme dans de nombreux outils similaires SQL Server (par exemple, SQLCMD), les paramètres sont passés à SqlLocalDB comme arguments de ligne de commande et la sortie est envoyée à la console.  
  
 SqlLocalDB permet aux développeurs d'utiliser LocalDB sans devoir écrire du code pour appeler l'API ou dépendre d'autres d'outils pour l'exécuter pour eux.  
  
## <a name="sqllocaldb-options"></a>Options de SqlLocalDB  
 SqlLocalDB prend en charge les options suivantes.  
  
|Option|Ce qu’il fait|  
|------------|------------------|  
|`-?`|Affiche le texte d'aide.|  
|`create&#124;c "instance name" [version-number] [-s]`|Crée une nouvelle instance de LocalDB avec un nom et une version spécifiés.<br /><br /> Si le paramètre [numéro-version] est omis, il prend par défaut la valeur de la version de la build de SqlLocalDB.<br /><br /> -s démarre la nouvelle instance de LocalDB après sa création.|  
|`delete&#124;d "instance name"`|Supprime l'instance de LocalDB portant le nom spécifié.|  
|`start&#124;s "instance name"`|Démarre l'instance de LocalDB portant le nom spécifié.|  
|`stop&#124;p "instance name" [-i&#124;-k]`|Arrête l'instance de LocalDB portant le nom spécifié, une fois les requêtes actuelles terminées.<br /><br /> -i demande l'arrêt de l'instance de LocalDB avec l'option NOWAIT.<br /><br /> -k met fin au processus de l'instance de LocalDB sans le contacter.|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|Partage l'instance privée spécifiée à l'aide du nom partagé spécifié. Si le SID ou le nom de compte de l'utilisateur est omis, il prend par défaut la valeur de l'utilisateur actuel.|  
|`unshare&#124;u "shared name"`|Annule le partage de l'instance de LocalDB partagée spécifiée.|  
|`info&#124;i`|Répertorie toutes les instances existantes de LocalDB détenues par l'utilisateur actuel et toutes les instances partagées de LocalDB.|  
|`info&#124;i "instance name"`|Affiche des informations relatives à l'instance de LocalDB spécifiée.|  
|`versions&#124;v`|Répertorie toutes les versions de LocalDB installées sur l'ordinateur.|  
|||  
|`trace&#124;t on&#124;off`|Active et désactive le traçage.|  
  
 SqlLocalDB traite les espaces comme des délimiteurs ; vous devez donc placer les noms d'instances contenant des espaces et des caractères spéciaux entre guillemets. Exemple :  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
