---
title: "Se connecter &#224; une instance de SQL Server (via l&#39;invite de commandes) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connexions [SQL Server], instance nommées de SQL Server"
  - "connexions [SQL Server]"
  - "connexions [SQL Server], instance par défaut de SQL Server"
  - "invite de commandes [SQL Server], connexions"
  - "connexion [SQL Server]"
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Se connecter &#224; une instance de SQL Server (via l&#39;invite de commandes)
  Cette rubrique explique comment tester la connectivité à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avec l'utilitaire **sqlcmd** .  
  
##  <a name="SSMSProcedure"></a>  
  
#### Pour se connecter à l’instance par défaut de SQL Server  
  
1.  À partir d'une invite de commandes, saisissez la commande suivante afin de vérifier vos informations d'identification par l'authentification Windows :  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### Pour se connecter à une instance nommée de SQL Server  
  
1.  À partir d'une invite de commandes, saisissez la commande suivante afin de vérifier vos informations d'identification par l'authentification Windows :  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## Voir aussi  
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Utilitaire osql](../../tools/osql-utility.md)  
  
  