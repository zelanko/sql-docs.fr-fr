---
title: "Option cancel (outil d&#39;administration Distributed Replay) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Option cancel (outil d&#39;administration Distributed Replay)
  L’outil d’administration [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay (**DReplay.exe**) est un outil en ligne de commande qui permet de communiquer avec Distributed Replay Controller. Cette rubrique décrit l’option de ligne de commande **cancel** et la syntaxe correspondante.  
  
 L’option **cancel** annule l’opération en cours d’exécution sur le contrôleur.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.png "Icône Lien de rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## Syntaxe  
  
```  
  
dreplay cancel [-m controller] [-q]   
```  
  
#### Paramètres  
 **-m** *controller*  
 Nom de l'ordinateur du contrôleur. Vous pouvez utiliser « `localhost` » ou « `.` » pour désigner l'ordinateur local.  
  
 Si le paramètre **-m** n’est pas spécifié, l’ordinateur local est utilisé.  
  
 **-q**  
 Mode silencieux. N'invite à aucune confirmation.  
  
 Le paramètre **-q** est facultatif.  
  
## Exemples  
 Dans l'exemple suivant, une demande d'annulation est soumise en mode silencieux. La valeur `localhost` indique que le service contrôleur s'exécute sur le même ordinateur que l'outil d'administration.  
  
```  
dreplay cancel –m localhost -q  
```  
  
## Autorisations  
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.  
  
 Pour plus d’informations, voir [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## Voir aussi  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  