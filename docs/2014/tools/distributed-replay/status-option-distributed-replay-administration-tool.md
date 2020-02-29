---
title: Option status (outil d’administration Distributed Replay) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e56a5229f0f26dfe701a425653b3d7f5a4ece842
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78171938"
---
# <a name="status-option-distributed-replay-administration-tool"></a>Option status (outil d'administration Distributed Replay)
  L' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outil d’administration Distributed Replay `DReplay.exe`,, est un outil en ligne de commande que vous pouvez utiliser pour communiquer avec le contrôleur Distributed Replay. Cette rubrique décrit l’option de ligne de commande **status** et la syntaxe correspondante.

 L'option **status** interroge le contrôleur et affiche l'état en cours.

 ![Icône de lien vers une rubrique](../../database-engine/media/topic-link.gif "Icône du lien de rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Syntaxe

```

dreplay status [-mcontroller] [-fstatus_interval]
```

#### <a name="parameters"></a>Paramètres
 **-m** *contrôleur* spécifie le nom d’ordinateur du contrôleur. Vous pouvez utiliser «`localhost`» ou «`.`» pour désigner l'ordinateur local.

 Si le paramètre **-m** n’est pas spécifié, l’ordinateur local est utilisé.

 **-f** *status_interval* spécifie la fréquence (en secondes) à laquelle afficher l’État.

 Si le paramètre **-f** n’est pas spécifié, l’intervalle par défaut est de 30 secondes.

## <a name="examples"></a>Exemples
 Dans l'exemple suivant, l'état en cours est affiché toutes les 60 secondes. La valeur `localhost` indique que le service contrôleur s'exécute sur le même ordinateur que l'outil d'administration.

```
dreplay status -m localhost -f 60
```

## <a name="permissions"></a>Autorisations
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.

 Pour plus d’informations, voir [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>Voir aussi
 [SQL Server Distributed Replay](sql-server-distributed-replay.md) [débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)


