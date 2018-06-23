---
title: Boîte de dialogue informations d’emprunt d’identité (Assistant Importation de Table) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c53b71a06904bd3f898efa3dd2d9946670193845
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140404"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Boîte de dialogue Informations d'emprunt d'identité (Assistant Importation de table)
  Utilisez la page **Informations d'emprunt d'identité** pour spécifier les informations d'identification que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilisera pour se connecter à la source de données. Pour plus d’informations sur l’emprunt d’identité d’informations d’identification, consultez [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Options  
 **Mot de passe et le nom d’utilisateur Windows spécifique**  
 Sélectionnez cette option pour que le modèle tabulaire utilise les informations d'identification de sécurité d'un compte d'utilisateur Windows spécifié.  
  
 **Nom d'utilisateur**  
 Entrez le domaine et le nom du compte d'utilisateur à utiliser. Utilisez le format suivant :  
  
 *\<Nom de domaine >* **\\**  *\<nom de compte d’utilisateur >*  
  
 Cette option est activée si **Utiliser un nom d'utilisateur et un mot de passe spécifiques** est sélectionné.  
  
 **Mot de passe**  
 Tapez le mot de passe du compte d'utilisateur que doit utiliser le modèle tabulaire.  
  
 Cette option est activée si **Utiliser un nom d'utilisateur et un mot de passe spécifiques** est sélectionné.  
  
 **Compte de service**  
 Sélectionnez cette option pour utiliser les informations d’identification de sécurité associées au service [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère le modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [L’emprunt d’identité &#40;SSAS tabulaire&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  