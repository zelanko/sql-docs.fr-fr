---
title: Sélectionner un package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 026c588f2fc35a6cb256a63046ad91e5d1b5641a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62830246"
---
# <a name="select-a-package"></a>Sélectionner un package
  Utilisez la boîte de dialogue **Sélectionner un package** pour spécifier le package à partir duquel la tâche MSMQ peut recevoir des messages.  
  
## <a name="static-options"></a>Options statiques  
 **Lieu**  
 Spécifiez l'emplacement du package. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Définissez l'emplacement d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La sélection de cette valeur affiche les options dynamiques, **Serveur**, **Utiliser l'authentification Windows**, **Utiliser l'authentification SQL Server**, **Nom d'utilisateur**et **Mot de passe**.|  
|Fichier DTSX|Définissez l'emplacement d'un fichier DTSX. La sélection de cette valeur affiche l'option dynamique **Nom de fichier**.|  
  
## <a name="location-dynamic-options"></a>Options dynamiques pour la définition de l'emplacement  
  
### <a name="location--sql-server"></a>Emplacement = SQL Server  
 **Nom du package**  
 Sélectionnez un package stocké sur le serveur spécifié.  
  
 **Serveur**  
 Tapez le nom d'un serveur ou sélectionnez-en un dans la liste.  
  
 **Utiliser l'authentification Windows**  
 Cliquez pour utiliser l'authentification Windows.  
  
 **Utiliser l’authentification SQL Server**  
 Cliquez pour utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Nom d'utilisateur**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fournissez un nom d’utilisateur à utiliser pour ouvrir une session sur le serveur.  
  
 **Mot de passe**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un mot de passe.  
  
### <a name="location--dtsx-file"></a>Emplacement = Fichier DTSX  
 **Nom de fichier**  
 Indiquez le chemin d’un package ou cliquez sur le bouton Parcourir **(...)** pour rechercher le package.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche MSMQ](message-queue-task.md)  
  
  
