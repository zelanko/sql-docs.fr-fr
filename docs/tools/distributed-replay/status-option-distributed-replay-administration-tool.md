---
title: Option d’état dans l’outil d’administration
titleSuffix: SQL Server Distributed Replay
ms.prod: sql
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 35851ce2f16ba5cb0e96ba24e9e67c887efd4aaf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74992186"
---
# <a name="status-option-distributed-replay-administration-tool"></a>Option status (outil d'administration Distributed Replay)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’outil d’administration [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay, **DReplay.exe**, est un outil en ligne de commande qui permet de communiquer avec Distributed Replay Controller. Cette rubrique décrit l’option de ligne de commande **status** et la syntaxe correspondante.  
  
 L'option **status** interroge le contrôleur et affiche l'état en cours.  
  
 ![Icône de lien vers une rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dreplay status [-m controller] [-f status_interval]  
```  
  
#### <a name="parameters"></a>Paramètres  
 **-m** _controller_  
 Spécifie le nom de l'ordinateur du contrôleur. Vous pouvez utiliser «`localhost`» ou «`.`» pour désigner l'ordinateur local.  
  
 Si le paramètre **-m** n’est pas spécifié, l’ordinateur local est utilisé.  
  
 **-f** _status_interval_  
 Spécifie la fréquence (en secondes) à laquelle afficher l'état.  
  
 Si le paramètre **-f** n’est pas spécifié, l’intervalle par défaut est de 30 secondes.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, l'état en cours est affiché toutes les 60 secondes. La valeur `localhost` indique que le service contrôleur s'exécute sur le même ordinateur que l'outil d'administration.  
  
```  
dreplay status -m localhost -f 60  
```  
  
## <a name="permissions"></a>Autorisations  
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.  
  
 Pour plus d’informations, voir [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)   
 [Débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  
