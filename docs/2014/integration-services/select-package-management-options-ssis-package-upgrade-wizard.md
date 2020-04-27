---
title: Sélectionner les options de Package Management (Assistant Mise à niveau de packages SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectpackagemgtoptions.f1
ms.assetid: 810fc020-51cd-43ed-9f35-af99b4f35947
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c71f254b0d0fb79e3ee8135c10d2d9ed715d3437
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66056031"
---
# <a name="select-package-management-options-ssis-package-upgrade-wizard"></a>Sélectionner les options de gestion des packages (Assistant Mise à niveau de packages SSIS)
  Utilisez la page **Sélectionner les options de gestion des packages** pour spécifier des options permettant de mettre à niveau des packages.  
  
 **Pour exécuter l'Assistant Mise à niveau de packages SSIS**  
  
-   [Mettre à niveau des packages Integration Services à l'aide de l'Assistant Mise à niveau de packages SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="options"></a>Options  
 **Mettre à jour les chaînes de connexion pour l'utilisation des nouveaux noms de fournisseurs**  
 Mettez à jour les chaînes de connexion afin d'utiliser les noms des fournisseurs suivants pour la version actuelle d' [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
-   Fournisseur OLE DB pour [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 L'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] met à jour uniquement les chaînes de connexion qui sont stockées dans des gestionnaires de connexions. Il ne met pas à jour les chaînes de connexion qui sont construites dynamiquement à l'aide du langage d'expression [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou en utilisant du code dans une tâche de script.  
  
 **Valider les packages mis à niveau**  
 Validez les packages de mise à niveau et enregistrez uniquement ceux dont la validation a réussi.  
  
 Si vous ne sélectionnez pas cette option, l'Assistant ne validera pas les packages de mise à niveau. Par conséquent, il les enregistrera tous, qu'ils soient valides ou non. L’Assistant enregistre les packages de mise à niveau dans la destination spécifiée dans la page **Sélectionner l’emplacement de destination** de l’Assistant.  
  
 La validation ralentit le processus de mise à niveau. Nous vous recommandons de ne pas sélectionner cette option pour les packages volumineux qui sont susceptibles d'être mis à niveau avec succès.  
  
 **Créer des ID de package**  
 Créez de nouveaux ID de package pour les packages de mise à niveau.  
  
 **Continuer le processus de mise à niveau lorsque la mise à niveau d’un package échoue**  
 Spécifiez que, quand un package ne peut pas être mis à niveau, l’Assistant Mise à niveau de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] continue à mettre à niveau les packages restants.  
  
 **Conflits de noms de packages**  
 Spécifiez la façon dont l'Assistant doit gérer les packages qui portent le même nom. Cette option a les valeurs répertoriées dans le tableau suivant.  
  
 **Remplacer les fichiers de packages existants**  
 Remplace le package existant par le package de mise à niveau du même nom.  
  
 **Ajouter des suffixes numériques pour mettre à niveau les noms de packages**  
 Ajoute un suffixe numérique au nom du package de mise à niveau.  
  
 **Ne pas mettre à niveau les packages**  
 Arrête la mise à niveau des packages et affiche une erreur à la fin de l'Assistant.  
  
 Ces options ne sont pas disponibles quand vous sélectionnez l’option **Enregistrer à l’emplacement source** dans la page **Sélectionner l’emplacement de destination** de l’Assistant.  
  
 **Ignorer les configurations**  
 Ne charge pas les configurations de package pendant la mise à niveau des packages. L'activation de cette option réduit le temps requis pour mettre à niveau le package.  
  
 **Sauvegarder les packages d’origine**  
 Cette option demande à l’Assistant de sauvegarder les packages d’origine dans un dossier **SSISBackupFolder** . L’Assistant crée le dossier **SSISBackupFolder** en tant que sous-dossier du dossier qui contient les packages d’origine et les packages mis à niveau.  
  
> [!NOTE]  
>  Cette option est disponible uniquement lorsque vous spécifiez que les packages d'origine et les packages mis à niveau sont stockés dans le système de fichiers et dans le même dossier.  
  
 Pour plus d’informations, consultez [Mettre à niveau des packages Integration Services à l’aide de l’Assistant Mise à niveau de packages SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à niveau des packages Integration Services](install-windows/upgrade-integration-services-packages.md)  
  
  
