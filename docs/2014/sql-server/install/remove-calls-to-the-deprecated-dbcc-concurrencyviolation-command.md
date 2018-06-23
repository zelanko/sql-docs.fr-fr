---
title: Supprimez les appels à la commande DBCC CONCURRENCYVIOLATION déconseillée | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a17b3c844afb6b8b804da258b0330d45dc7208e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140220"
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
  