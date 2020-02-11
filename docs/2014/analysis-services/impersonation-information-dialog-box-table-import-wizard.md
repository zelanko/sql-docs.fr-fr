---
title: Boîte de dialogue informations d’emprunt d’identité (Assistant importation de table) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6592d81e91e0582c79bc1a8bb1264b6ab9a7b733
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66080697"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Boîte de dialogue Informations d'emprunt d'identité (Assistant Importation de table)
  Utilisez la page **Informations d'emprunt d'identité** pour spécifier les informations d'identification que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilisera pour se connecter à la source de données. Pour plus d’informations sur l’emprunt d’identité d’informations d’identification, consultez [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Options  
 **Nom d’utilisateur et mot de passe Windows spécifiques**  
 Sélectionnez cette option pour que le modèle tabulaire utilise les informations d'identification de sécurité d'un compte d'utilisateur Windows spécifié.  
  
 **Nom d'utilisateur**  
 Entrez le domaine et le nom du compte d'utilisateur à utiliser. Utilisez le format suivant :  
  
 Nom de **\\** domaine>* \<nom du compte d’utilisateur>* * \<*  
  
 Cette option est activée si **Utiliser un nom d'utilisateur et un mot de passe spécifiques** est sélectionné.  
  
 **Mot de passe**  
 Tapez le mot de passe du compte d'utilisateur que doit utiliser le modèle tabulaire.  
  
 Cette option est activée si **Utiliser un nom d'utilisateur et un mot de passe spécifiques** est sélectionné.  
  
 **Compte de service**  
 Sélectionnez cette option pour utiliser les informations d’identification de sécurité associées au service [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère le modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Emprunt d’identité &#40;&#41;tabulaire SSAS](tabular-models/impersonation-ssas-tabular.md)  
  
  
