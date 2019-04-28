---
title: Renommer l’utilisateur système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8e227e4d382dac627626b977427aae05d0295744
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855320"
---
# <a name="rename-user-sys"></a>Renommer l'utilisateur système
  Le Conseiller de mise à niveau a détecté le nom d'utilisateur **sys** dans une base de données. Ce nom est réservé. Renommez l'utilisateur avant d'effectuer la mise à niveau. Si l'utilisateur n'est pas renommé, la base de données sera marquée comme étant suspecte après l'opération de mise à niveau et restera indisponible jusqu'à ce qu'elle soit mise en ligne.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 L'utilisateur **sys** est réservé.  
  
## <a name="corrective-action"></a>Action corrective  
  
### <a name="before-upgrade-procedure"></a>Procédure avant mise à niveau  
 Avant la mise à niveau, dans chaque base de données qui contient l'utilisateur **sys**, procédez comme suit :  
  
1.  Créez un nouvel utilisateur.  
  
2.  Utilisez les instructions suivantes pour afficher toutes les autorisations accordées par l'utilisateur **sys** et accordées à l'utilisateur **sys**.  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  Pour transférer l'appartenance de tous les objets possédés par **sys** au nouvel utilisateur, utilisez **sp_changeobjectowner**.  
  
4.  Supprimez l'utilisateur **sys**.  
  
5.  Pour restaurer les autorisations d'origine capturées à l'étape 2, utilisez la clause AS *new_user* de l'instruction GRANT.  
  
6.  Modifiez les scripts pour qu'ils fassent référence au nouvel utilisateur. Par exemple, dans les scripts, des instructions telles que `SELECT * FROM sys.my`_`table` doivent être remplacées par `SELECT * FROM new_user.my_table`.  
  
### <a name="after-upgrade-procedure"></a>Procédure après mise à niveau  
 Si l'utilisateur **sys** n'a pas été renommé avant la mise à niveau, procédez comme suit :  
  
1.  Exécutez l'instruction `ALTER DATABASE db_name SET ONLINE`. La base de données se trouvera en mode SINGLE_USER.  
  
2.  Exécutez toutes les étapes répertoriées dans la section Procédure avant mise à niveau.  
  
3.  Exécutez l'instruction `ALTER DATABASE db_name SET MULTI_USER`.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
