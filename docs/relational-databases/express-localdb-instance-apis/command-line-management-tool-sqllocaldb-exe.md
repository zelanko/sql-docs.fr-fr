---
title: 'Outil de gestion en ligne de commande : SqlLocalDB.exe | Microsoft Docs'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c39272a1f8af7fce092f7aa31ac3a4f7ebd2263
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765252"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Outil de gestion en ligne de commande : SqlLocalDB.exe
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  SqlLocalDB.exe est un outil simple qui permet à l'utilisateur de gérer facilement les instances de LocalDB à partir de l'invite de commandes. Il est implémenté comme wrapper simple autour de l'API de l'instance de LocalDB. Comme dans de nombreux outils similaires SQL Server (par exemple, SQLCMD), les paramètres sont passés à SqlLocalDB comme arguments de ligne de commande et la sortie est envoyée à la console.  
  
 SqlLocalDB permet aux développeurs d'utiliser LocalDB sans devoir écrire du code pour appeler l'API ou dépendre d'autres d'outils pour l'exécuter pour eux.  
  
## <a name="sqllocaldb-options"></a>Options de SqlLocalDB  
 SqlLocalDB prend en charge les options suivantes.  
  
|Option|Résultat|  
|------------|------------------|  
|`-?`|Affiche le texte d'aide.|  
|`create\|c "instance name" [version-number] [-s]`|Crée une nouvelle instance de LocalDB avec un nom et une version spécifiés.<br /><br /> Si le paramètre [numéro-version] est omis, il prend par défaut la valeur de la version de la build de SqlLocalDB.<br /><br /> -s démarre la nouvelle instance de LocalDB après sa création.|  
|`delete\|d "instance name"`|Supprime l'instance de LocalDB portant le nom spécifié.|  
|`start\|s "instance name"`|Démarre l'instance de LocalDB portant le nom spécifié.|  
|`stop\|p "instance name" [-i\|-k]`|Arrête l'instance de LocalDB portant le nom spécifié, une fois les requêtes actuelles terminées.<br /><br /> -i demande l'arrêt de l'instance de LocalDB avec l'option NOWAIT.<br /><br /> -k met fin au processus de l'instance de LocalDB sans le contacter.|  
|`share\|h ["owner SID or account"] "private name" "shared name"`|Partage l'instance privée spécifiée à l'aide du nom partagé spécifié. Si le SID ou le nom de compte de l'utilisateur est omis, il prend par défaut la valeur de l'utilisateur actuel.|  
|`unshare\|u "shared name"`|Annule le partage de l'instance de LocalDB partagée spécifiée.|  
|`info\|i`|Répertorie toutes les instances existantes de LocalDB détenues par l'utilisateur actuel et toutes les instances partagées de LocalDB.|  
|`info\|i "instance name"`|Affiche des informations relatives à l'instance de LocalDB spécifiée.|  
|`versions\|v`|Répertorie toutes les versions de LocalDB installées sur l'ordinateur.|  
|||  
|`trace\|t on\|off`|Active et désactive le traçage.|  
  
 SqlLocalDB traite les espaces comme des délimiteurs ; vous devez donc placer les noms d'instances contenant des espaces et des caractères spéciaux entre guillemets. Par exemple :  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
