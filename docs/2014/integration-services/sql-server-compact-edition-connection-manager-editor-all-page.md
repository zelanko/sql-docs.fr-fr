---
title: Éditeur du gestionnaire de connexions de l’édition SQL Server Compact (page tout) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8a26587f9dd426cdf53a3a53a36d0e81e95ebf77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055470"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>Éditeur du gestionnaire de connexions SQL Server Compact Edition (page Tout)
  La boîte de dialogue **Éditeur du gestionnaire de connexions SQL Server Compact Edition** permet de spécifier les propriétés permettant de se connecter à une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 Pour en savoir plus sur le gestionnaire de connexions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition, consultez [Éditeur du gestionnaire de connexions SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## <a name="options"></a>Options  
 **Seuil de réduction automatique**  
 Spécifiez le pourcentage d’espace libre autorisé dans la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact avant que le processus de réduction automatique soit lancé.  
  
 **Escalade de verrous par défaut**  
 Spécifiez le nombre de verrous de base de données acquis par la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact avant qu’elle tente de promouvoir les verrous.  
  
 **Délai d’attente de verrouillage par défaut**  
 Spécifiez l'intervalle par défaut, en millisecondes, d'attente d'un verrou par une instruction.  
  
 **Intervalle de vidage**  
 Spécifiez l'intervalle, en secondes, s'écoulant entre les vidages de données de transactions validées sur le disque.  
  
 **Identificateur de paramètres régionaux**  
 Spécifiez l’identificateur de paramètres régionaux (LCID) de la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Taille maximale de la mémoire tampon**  
 Spécifiez la quantité maximale de mémoire (en Ko) utilisée par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact avant d’effectuer un vidage des données sur le disque.  
  
 **Taille maximale de la base de données**  
 Spécifiez la taille maximale (en Mo) de la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Mode**  
 Spécifiez le mode de fichier dans lequel ouvrir la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact. La valeur par défaut de cette propriété est **Read Write**.  
  
 L'option Mode comporte quatre valeurs, qui sont décrites dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Lecture seule**|Offre un accès en lecture seule à la base de données.|  
|**Lecture Écriture**|Autorise l'accès en lecture et écriture à la base de données.|  
|**Exclusif**|Offre un accès exclusif à la base de données.|  
|**Lecture partagée**|Indique que plusieurs utilisateurs peuvent lire la base de données simultanément.|  
  
 **Persist Security Info**  
 Indique si des informations de sécurité sont retournées dans la chaîne de connexion. La valeur par défaut de cette option est **False**.  
  
 **Répertoire des fichiers temporaires**  
 Spécifiez l’emplacement du fichier de base de données temporaire de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Source de données**  
 Spécifiez le nom de la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Mot de passe**  
 Entrez le mot de passe pour la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions de l’édition de SQL Server Compact &#40;page connexion&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
