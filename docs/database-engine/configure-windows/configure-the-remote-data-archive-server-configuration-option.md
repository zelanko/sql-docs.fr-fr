---
title: "Configurer l’option de configuration de serveur remote data archive | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 528a76ce80fdace23f76b2b221165f190a5ead5d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>Configurer l’option de configuration de serveur remote data archive
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **remote data archive** afin d’indiquer si les tables et les bases de données du serveur peuvent être activées pour Stretch. Pour plus d'informations, consultez [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 L’option **remote data archive** autorise les valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Les bases de données et les tables du serveur ne peuvent pas être activées pour Stretch.|  
|1|Les bases de données et les tables du serveur peuvent être activées pour Stretch.|  
  
 L’exécution de **sp_configure** pour définir la valeur de l’option **Archive de données distante** nécessite des autorisations sysadmin ou serveradmin.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche tout d’abord le paramètre actuel de l’option **remote data archive** . L’exemple active ensuite l’option **remote data archive** en définissant sa valeur sur 1.  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 Pour désactiver l'option, affectez-lui la valeur 0.  
  
## <a name="see-also"></a>Voir aussi  
 [Activer Stretch Database pour une base de données](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

