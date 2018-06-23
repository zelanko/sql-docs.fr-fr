---
title: Supprimer un groupe de charge de travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 793052419843c2e2421458da07b2815932683645
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039732"
---
# <a name="delete-a-workload-group"></a>Supprimer un groupe de charge de travail
  Vous pouvez supprimer un groupe de charge de travail ou un pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de Transact-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **Pour supprimer un groupe de charge de travail, utilisez :**  [Explorateur d’objets](#DelWGObjEx), [Propriétés de Resource Governor](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Vous ne pouvez pas supprimer un groupe de charge de travail s'il contient des sessions actives.  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Si un groupe de charge de travail contient des sessions actives, sa suppression ou son déplacement vers un pool de ressources différent échoue lorsque l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE est appelée pour appliquer la modification. Pour éviter ce problème, vous pouvez suivre l'une des actions suivantes :  
  
-   Attendez la déconnexion de toutes les sessions du groupe affecté, puis réexécutez l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Arrêtez explicitement les sessions du groupe affecté à l'aide de la commande KILL, puis réexécutez l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE. Si vous décidez que vous ne souhaitez pas arrêter des sessions explicitement après avoir utilisé **Supprimer** mais avant d’arrêter des sessions actives, recréez le groupe en utilisant le nom d’origine et déplacez le groupe vers le pool de ressources d’origine.  
  
-   Redémarrez le serveur. Au terme du processus de redémarrage, le groupe supprimé ne sera pas créé, et un groupe déplacé utilisera la nouvelle affectation de pool de ressources.  
  
###  <a name="Permissions"></a> Permissions  
 La suppression d'un groupe de charge de travail nécessite l'autorisation CONTROL SERVER.  
  
##  <a name="DelWGObjEx"></a> Supprimer un groupe de charge de travail à l'aide de l'Explorateur d'objets  
 **Pour supprimer un groupe de charge de travail à l'aide de l'Explorateur d'objets**  
  
1.  Dans[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets, développez de manière récursive le nœud **Gestion** jusqu'à **Pools de ressources**.  
  
2.  Développez de manière récursive **Pools de ressources** vers le bas et en incluant le nœud **Groupes de charge de travail** dans le pool de ressources qui contient le groupe de charge de travail à supprimer.  
  
3.  Cliquez avec le bouton droit sur le groupe de charge de travail, puis cliquez sur **Supprimer**.  
  
4.  Dans la fenêtre **Supprimer un objet** , le groupe de charge de travail est répertorié dans la liste **Objet à supprimer** . Pour supprimer le groupe de charge de travail, cliquez sur **OK**.  
  
##  <a name="DelWGRGProp"></a> Supprimer un groupe de charge de travail à l'aide des propriétés de Resource Governor  
 **Pour supprimer un groupe de charge de travail à l'aide de la page Propriétés de Resource Governor**  
  
1.  Dans l'Explorateur d'objets, développez de manière récursive le nœud **Gestion** jusqu'à **Pools de ressources**inclus.  
  
2.  Cliquez avec le bouton droit sur le pool de ressources qui contient le groupe de charge de travail à supprimer, puis cliquez sur **Propriétés**. Cette procédure ouvre la page **Propriétés de Resource Governor** .  
  
3.  Dans la fenêtre **Groupes de charge de travail pour le pool de ressources** , cliquez sur la ligne du groupe de charge de travail à supprimer, puis cliquez avec le bouton droit sur la flèche droite à gauche de la ligne et sélectionnez **Supprimer**.  
  
4.  Pour supprimer le groupe de charge de travail, cliquez sur **OK**.  
  
##  <a name="DelWGTSQL"></a> Supprimer un groupe de charge de travail à l'aide de Transact-SQL  
 **Pour supprimer un groupe de charge de travail à l'aide de Transact-SQL**  
  
1.  Exécuter la `DROP WORKLOAD GROUP` instruction en spécifiant le nom du groupe de charges de travail à supprimer.  
  
2.  Avant d'émettre l'instruction `ALTER RESOURCE GOVERNOR RECONFIGURE`, vérifiez qu'il n'y a pas de demandes actives dans le groupe de charge de travail en cours de suppression. S’il existe des demandes actives, `ALTER RESOURCE GOVERNOR` échoue. Pour éviter ce problème, vous pouvez effectuer l'une des actions suivantes :  
  
    -   Attendez jusqu'à ce que toutes les sessions du groupe de charges de travail soient déconnectées.  
  
    -   Arrêtez explicitement les sessions dans le groupe de charge de travail à l'aide de la commande `KILL`.  
  
    -   Redémarrez le serveur. Le groupe de charge de travail ne sera pas recréé.  
  
    -   Dans un scénario dans lequel vous avez émis l'instruction `DROP WORKLOAD GROUP` mais décidez que vous ne souhaitez pas arrêter explicitement des sessions pour appliquer la modification, vous pouvez recréer le groupe en utilisant le nom qu'il portait avant l'émission de l'instruction DROP, puis déplacer le groupe dans le pool de ressources d'origine.  
  
3.  Exécuter la `ALTER RESOURCE GOVERNOR RECONFIGURE` instruction.  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant supprime un groupe de charge de travail nommé `groupAdhoc`.  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Créer un pool de ressources](create-a-resource-pool.md)   
 [Créer un groupe de charge de travail](create-a-workload-group.md)   
 [Supprimer un pool de ressources](delete-a-resource-pool.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
