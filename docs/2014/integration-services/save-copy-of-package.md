---
title: Enregistrer une copie du Package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0cd386cad85726707f1ce3ea9f7931bda4e66c25
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140499"
---
# <a name="save-copy-of-package"></a>Enregistrer une copie du package
  La boîte de dialogue **Enregistrer une copie du package**, accessible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], permet d’enregistrer la copie d’un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] vers un emplacement différent et éventuellement de modifier le niveau de protection du package.  
  
## <a name="options"></a>Options  
 **Emplacement du package**  
 Sélectionnez le type d'emplacement de stockage dans lequel enregistrer la copie du package. Les options suivantes sont disponibles :  
  
 **SQL Server**  
  
 **Système de fichiers**  
  
 **Magasin de packages SSIS**  
  
 **Server**  
 Tapez le nom d’un serveur ou sélectionnez-en un dans la liste. Cette option est disponible uniquement si l’emplacement de stockage est **SQL Server** ou **Magasin de packages SSIS**.  
  
 **Authentification**  
 Sélectionnez l'authentification Windows ou l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Cette option est disponible uniquement si l’emplacement de stockage est [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  À chaque fois que possible, utilisez l'authentification Windows.  
  
 **Type d'authentification**  
 Sélectionnez un type d'authentification.  
  
 **Nom d'utilisateur**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , entrez un nom d’utilisateur.  
  
 **Mot de passe**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , entrez un mot de passe.  
  
 **Chemin d'accès au package**  
 Tapez le chemin du package ou cliquez sur le bouton Parcourir **(…)** pour rechercher le dossier dans lequel stocker le package.  
  
 **Niveau de protection**  
 Cliquez sur le bouton Parcourir **(…)** et mettez à jour le niveau de protection dans la boîte de dialogue **Niveau de protection du package** . Pour plus d’informations, consultez [Boîte de dialogue Niveau de protection du package](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’interface utilisateur de la boîte de dialogue Importation Package](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [Exporter la référence de l’interface utilisateur de la boîte de dialogue Package](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Enregistrer des packages](save-packages.md)   
 [Importer et exporter des Packages &#40;Service SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
