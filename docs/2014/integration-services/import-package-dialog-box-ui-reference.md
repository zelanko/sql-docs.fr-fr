---
title: Importer la référence de l’interface utilisateur de la boîte de dialogue Package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f7bb152f19bd2ed5e482cff2e57806c1653ef415
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227729"
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
 Tapez le chemin du package ou cliquez sur le bouton Parcourir **(…)** pour rechercher le package.  
  
 **Nom du package**  
 Éventuellement, renommez le package. Par défaut, son nom est celui du package à importer.  
  
 **Niveau de protection**  
 Cliquez sur le bouton Parcourir **(…)** et, dans la boîte de dialogue **Niveau de protection du package** , mettez à jour le niveau de protection. Pour plus d’informations, consultez [Boîte de dialogue Niveau de protection du package](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer une copie du Package](../../2014/integration-services/save-copy-of-package.md)   
 [Exporter la référence de l’interface utilisateur de la boîte de dialogue Package](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Enregistrer des packages](save-packages.md)   
 [Importer et exporter des Packages &#40;Service SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
