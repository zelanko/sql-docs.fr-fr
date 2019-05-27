---
title: Supprimez les appels à la commande DBCC CONCURRENCYVIOLATION déconseillée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0110d4bc138ad0da953eb83d3c81ec265d2fd3ba
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093204"
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
  
