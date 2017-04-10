---
title: "Gestionnaire de connexions de fichiers | Microsoft Docs"
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
  - "dossiers [Integration Services], connexions"
  - "fichiers [Integration Services], connexions"
  - "fichiers [Integration Services]"
  - "gestionnaires de connexions [Integration Services], fichier"
  - "connexions [Integration Services], fichiers"
  - "Gestionnaire de connexions de fichiers"
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Gestionnaire de connexions de fichiers
  Un gestionnaire de connexions de fichiers permet à un package de référencer un fichier ou dossier existant ou de créer un fichier ou dossier au moment de l'exécution. Par exemple, vous pouvez référencer un fichier Excel. Certains composants de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent les informations figurant dans les fichiers pour réaliser leur travail. Par exemple, une tâche d'exécution SQL peut référencer un fichier contenant les instructions SQL exécutées par la tâche. D'autres composants exécutent des opérations sur les fichiers. Par exemple, la tâche de système de fichiers peut référencer un fichier pour le copier à un nouvel emplacement.  
  
## Types d'utilisations du gestionnaire de connexions de fichiers  
 La propriété **FileUsageType** du gestionnaire de connexions de fichiers spécifie la manière dont la connexion de fichiers est utilisée. Le gestionnaire de connexions de fichiers peut créer un fichier, créer un dossier, utiliser un fichier existant ou utiliser un dossier existant.  
  
 Le tableau suivant répertorie les valeurs de **FileUsageType**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Le gestionnaire de connexions de fichiers utilise un fichier existant.|  
|**1**|Le gestionnaire de connexions de fichiers crée un fichier.|  
|**2**|Le gestionnaire de connexions de fichiers utilise un dossier existant.|  
|**3**|Le gestionnaire de connexions de fichiers crée un dossier.|  
  
## Connexions de fichiers ou de dossiers multiples  
 Le gestionnaire de connexions de fichiers peut référencer un seul fichier ou dossier. Pour référencer plusieurs fichiers ou dossiers, utilisez un gestionnaire de connexions de fichiers multiples au lieu du gestionnaire de connexions de fichiers. Pour plus d’informations, consultez [Gestionnaire de connexions de fichiers multiples](../../integration-services/connection-manager/multiple-files-connection-manager.md).  
  
## Configuration du gestionnaire de connexions de fichiers  
 Lorsque vous ajoutez un gestionnaire de connexions de fichiers à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion de fichiers au moment de l’exécution, définit les propriétés de la connexion de fichiers et ajoute la connexion de fichiers à la collection **Connections** du package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **FILE**.  
  
 Vous pouvez configurer un gestionnaire de connexions de fichiers de plusieurs manières :  
  
-   Spécifiez le type d'utilisation.  
  
-   Spécifiez un fichier ou un dossier.  
  
 Vous pouvez définir la propriété ConnectionString du gestionnaire de connexions de fichiers en spécifiant une expression dans la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Toutefois, pour éviter une erreur de validation lorsque vous utilisez une expression pour spécifier le fichier ou dossier, dans **l’Éditeur du gestionnaire de connexions de fichiers**, pour **Fichier/Dossier**, ajoutez un chemin de fichier ou de dossier.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], consultez [Éditeur du gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programmation](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  