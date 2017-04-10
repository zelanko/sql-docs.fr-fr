---
title: "Gestionnaire de connexions SMO | Microsoft Docs"
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
  - "connexions [Integration Services], SMO"
  - "Gestionnaire de connexions SMO"
  - "gestionnaires de connexions [Integration Services], SMO"
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Gestionnaire de connexions SMO
  Un gestionnaire de connexions SMO permet à un package de se connecter à un serveur SMO (SQL Management Object). Les tâches de transfert incluses dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent un gestionnaire de connexions SMO. Par exemple, la tâche de transfert de connexions qui transfère des connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un gestionnaire de connexions SMO.  
  
 Quand vous ajoutez un gestionnaire de connexions SMO à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui est résolu en tant que connexion SMO au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connexions** sur le package. La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **SMOServer**.  
  
 Vous pouvez configurer le gestionnaire de connexions SMO de plusieurs manières :  
  
-   Spécifiez le nom d'un serveur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
-   Sélectionnez le mode d'authentification pour la connexion au serveur.  
  
## Configuration du gestionnaire de connexions SMO  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], consultez [Éditeur du gestionnaire de connexions SMO](../../integration-services/connection-manager/smo-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  