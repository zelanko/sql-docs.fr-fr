---
title: Importer la référence de l’interface utilisateur de la boîte de dialogue Package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3e36fae15f6f4220565bcc3d14c0e125ca6818f0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058082"
---
# <a name="import-package-dialog-box-ui-reference"></a>Référence de l'interface utilisateur de la boîte de dialogue Importer un package
  Utilisez la boîte de dialogue **Importer un package**, disponible dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], pour importer un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et pour définir ou modifier son niveau de protection.  
  
## <a name="options"></a>Options  
 **Emplacement du package**  
 Sélectionnez le type d'emplacement de stockage dans lequel importer le package. Les options suivantes sont disponibles :  
  
 **SQL Server**  
  
 **Système de fichiers**  
  
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
 Tapez le chemin du package ou cliquez sur le bouton Parcourir **(...)** pour rechercher le package.  
  
 **Nom du package**  
 Éventuellement, renommez le package. Par défaut, son nom est celui du package à importer.  
  
 **Niveau de protection**  
 Cliquez sur le bouton Parcourir **(...)** et, dans la boîte de dialogue **Niveau de protection du package**, mettez à jour le niveau de protection. Pour plus d’informations, consultez [Boîte de dialogue Niveau de protection du package](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer une copie du package](../../2014/integration-services/save-copy-of-package.md)   
 [Référence de l'interface utilisateur de la boîte de dialogue Exporter un package](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Enregistrer des packages](save-packages.md)   
 [Importer et exporter des packages &#40;service SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
