---
title: "Gestionnaire de connexions de SQL Server Compact Edition | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Compact, gestionnaire de connexions"
  - "connexions [Integration Services], SQL Server Compact"
  - "gestionnaires de connexions [Integration Services], SQL Server Compact"
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Gestionnaire de connexions de SQL Server Compact Edition
  Un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact permet à un package de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise ce gestionnaire de connexions pour charger des données dans une table d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, vous devez exécuter les packages qui se connectent à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact en mode 32 bits. Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact utilisé par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour se connecter à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact n’est disponible qu’en version 32 bits.  
  
## Configuration du gestionnaire de connexions SQL Server Compact Edition  
 Quand vous ajoutez un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui est résolu en connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connexions** du package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a la valeur **SQLMOBILE**.  
  
 Vous pouvez configurer le gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion qui indique l’emplacement de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
-   Spécifiez un mot de passe pour une base de données protégée par mot de passe.  
  
-   Spécifiez le serveur où est stockée la base de données.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur du gestionnaire de connexions SQL Server Compact Edition &#40;page Connexion&#41;](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [Éditeur du gestionnaire de connexions SQL Server Compact Edition &#40;page Tout&#41;](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programmation](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  