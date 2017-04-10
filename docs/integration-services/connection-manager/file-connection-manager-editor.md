---
title: "&#201;diteur du gestionnaire de connexions de fichiers | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.fileconnectionmanager.f1"
helpviewer_keywords: 
  - "Éditeur du gestionnaire de connexions de fichiers"
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# &#201;diteur du gestionnaire de connexions de fichiers
  Utilisez la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers** pour spécifier les propriétés à utiliser pour se connecter à un fichier ou à un dossier.  
  
> [!NOTE]  
>  Vous pouvez définir la propriété ConnectionString du gestionnaire de connexions de fichiers en spécifiant une expression dans la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Toutefois, pour éviter une erreur de validation quand vous utilisez une expression pour spécifier le fichier ou dossier, dans **l’Éditeur du gestionnaire de connexions de fichiers**, pour **Fichier/Dossier**, ajoutez un chemin du fichier ou du dossier.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers, consultez [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
## Options  
 **Type d'utilisation**  
 Indiquez si le **Gestionnaire de connexions de fichiers** se connecte à un fichier ou dossier existant ou s’il crée un nouveau fichier ou dossier.  
  
|Value|Description|  
|-----------|-----------------|  
|Créer un fichier|Crée un nouveau fichier au moment de l'exécution.|  
|Fichier existant|Utilise un fichier existant.|  
|Créer un dossier|Crée un nouveau dossier au moment de l'exécution.|  
|Dossier existant|Utilise un dossier existant.|  
  
 **Fichier / Dossier**  
 Si **Fichier**, spécifiez le fichier à utiliser.  
  
 Si **Dossier**, spécifiez le dossier à utiliser.  
  
 **Parcourir**  
 Sélectionnez le fichier ou le dossier à l’aide de la boîte de dialogue **Sélectionner un fichier** ou **Rechercher un dossier**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
  
  