---
title: Erreur WMI 0x8007052f | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d6e857e0ccaad9b6f34bbdc9b88aea2e6d7291d8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048835"
---
# <a name="wmi-error-0x8007052f"></a>Erreur WMI 0x8007052f
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|0x8007052f|  
|Source de l’événement|Erreur du fournisseur WMI|  
|Composant|Gestionnaire de configuration SQL Server|  
|Nom symbolique|N/D|  
|Texte du message|Échec d'ouverture de session : restriction de compte d'utilisateur. Parmi les explications possibles figurent les mots de passe vides qui ne sont pas autorisés, les restrictions liées aux heures de connexion ou l'application d'une restriction de stratégie.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur peut se produire lors de l'utilisation du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour basculer vers les comptes intégrés (Service réseau, Service local ou Système Local) lorsque [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est exécuté sur un cluster de serveurs Windows Server ou un contrôleur de domaine Windows Server. N'exécutez pas de services sous les comptes intégrés sur un cluster de serveurs Windows Server ou un contrôleur de domaine Windows Server. Pour obtenir des recommandations sur les comptes de service, consultez la rubrique « Configuration des comptes de service Windows » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Configurez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour utiliser un compte de domaine.  
  
  
