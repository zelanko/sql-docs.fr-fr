---
title: Supprimez les appels à la commande DBCC CONCURRENCYVIOLATION déconseillée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 574b3de41498fa24d2cbd913899d4d071cca6053
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203549"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>Supprimer les appels à la commande DBCC CONCURRENCYVIOLATION déconseillée
  Le Conseiller de mise à niveau a détecté l'utilisation de la commande DBCC CONCURRENCYVIOLATION. Cette commande n'est plus disponible. L'exécution de cette commande retourne l'erreur 2526.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Aucune version récente ou édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'inclut un administrateur de charge de travail ; par conséquent, la commande a été supprimée.  
  
## <a name="corrective-action"></a>Action corrective  
 Mettez à jour les applications et les scripts pour supprimer les références à cette commande déconseillée.  
  
## <a name="external-resources"></a>Ressources externes  
  
