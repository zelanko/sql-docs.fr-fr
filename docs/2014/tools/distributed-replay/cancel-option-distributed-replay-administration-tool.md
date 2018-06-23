---
title: Option cancel (outil d’administration Distributed Replay) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c839569ba6b67733610118a35d06c0872c9c8cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052536"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>Option cancel (outil d'administration Distributed Replay)
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outil d’administration Distributed Replay, `DReplay.exe`, est un outil de ligne de commande que vous pouvez utiliser pour communiquer avec distributed replay controller. Cette rubrique décrit l’option de ligne de commande **cancel** et la syntaxe correspondante.  
  
 L’option **cancel** annule l’opération en cours d’exécution sur le contrôleur.  
  
 ![Icône de lien vers une rubrique](../../database-engine/media/topic-link.gif "Icône de lien vers une rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dreplay cancel [-mcontroller] [-q]   
```  
  
#### <a name="parameters"></a>Paramètres  
 **-m** *controller*  
 Nom de l'ordinateur du contrôleur. Vous pouvez utiliser «`localhost`» ou «`.`» pour désigner l'ordinateur local.  
  
 Si le paramètre **-m** n’est pas spécifié, l’ordinateur local est utilisé.  
  
 **-q**  
 Mode silencieux. N'invite à aucune confirmation.  
  
 Le paramètre **-q** est facultatif.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, une demande d'annulation est soumise en mode silencieux. La valeur `localhost` indique que le service contrôleur s'exécute sur le même ordinateur que l'outil d'administration.  
  
```  
dreplay cancel –m localhost -q  
```  
  
## <a name="permissions"></a>Autorisations  
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.  
  
 Pour plus d’informations, voir [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)  
  
  
