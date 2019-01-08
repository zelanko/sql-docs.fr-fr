---
title: Exporter la référence de l’interface utilisateur de la boîte de dialogue Package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.exportpackage.f1
helpviewer_keywords:
- Export Package dialog box
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 91a7d5573a6d0488b48d7e4ddaf328664de7a2c8
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523667"
---
# <a name="export-package-dialog-box-ui-reference"></a>Référence de l'interface utilisateur de la boîte de dialogue Exporter un package
  Utilisez la boîte de dialogue **Exporter un package**, disponible dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], pour exporter un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vers un autre emplacement et éventuellement modifier son niveau de protection.  
  
## <a name="options"></a>Options  
 **Emplacement du package**  
 Sélectionnez le type de stockage vers lequel exporter le package. Les options suivantes sont disponibles :  
  
 **SQL Server**  
  
 **File System**  
  
 **Magasin de packages SSIS**  
  
 **Server**  
 Tapez le nom d’un serveur ou sélectionnez-en un dans la liste.  
  
 **Authentification**  
 Sélectionnez l'authentification Windows ou l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Cette option est disponible uniquement si l’emplacement de stockage est [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Dans la mesure du possible, utilisez l’authentification Windows.  
  
 **Type d'authentification**  
 Sélectionnez un type d'authentification.  
  
 **Nom d'utilisateur**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , entrez un nom d’utilisateur.  
  
 **Mot de passe**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , entrez un mot de passe.  
  
 **Chemin d'accès au package**  
 Tapez le chemin du package ou cliquez sur le bouton Parcourir **(...)** pour rechercher le dossier dans lequel stocker le package.  
  
 **Niveau de protection**  
 Cliquez sur le bouton Parcourir **(...)** et mettez à jour le niveau de protection dans la boîte de dialogue **Niveau de protection du package**. Pour plus d’informations, consultez [Boîte de dialogue Niveau de protection du package](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer une copie du package](../../2014/integration-services/save-copy-of-package.md)   
 [Référence de l'interface utilisateur de la boîte de dialogue Importer un package](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [Enregistrer des packages](save-packages.md)   
 [Importer et exporter des packages &#40;service SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
