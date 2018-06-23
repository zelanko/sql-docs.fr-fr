---
title: Boîte de dialogue Propriétés de connexion (SSAS - tabulaire) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.ssmsimbi.ConnectionProperties.F1
ms.assetid: 17bae8ae-2ba0-4978-be70-61c687f59d54
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5eee3a4fd0e915a875bcbac1d0215e435c10e04a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139509"
---
# <a name="connection-properties-dialog-box-ssas---tabular"></a>Boîte de dialogue Propriétés de connexion (SSAS - Tabulaire)
  Utilisez cette page pour consulter ou modifier dans SQL Server Management Studio les propriétés de connexion d'une source de données utilisée par une base de données model tabulaire.  
  
 Cette boîte de dialogue fournit des horodateurs et d'autres informations descriptives, ainsi que des propriétés personnalisables qui déterminent les caractéristiques de la connexion.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom**|Spécifie le nom de la source de données.|  
|**ID**|Affiche l'identificateur de l'objet de source de données.|  
|**Description**|Affiche la description de l'objet de source de données.|  
|**Créer un horodateur**|Affiche la date et l'heure de création de la base de données.|  
|**Dernière mise à jour du schéma**|Affiche la date et l'heure de la dernière mise à jour des métadonnées de la base de données.|  
|**Chaîne de connexion**|Affiche la chaîne de connexion utilisée pour se connecter à la source de données qui fournit des données au modèle.|  
|**Nombre maximal de connexions**|Spécifie le nombre maximal de connexions clientes à cette base de données.|  
|**Isolement**|Les valeurs valides sont ReadCommitted ou Snapshot. Pour plus d’informations, consultez [Isolation, élément &#40;ASSL&#41;](scripting/properties/isolation-element-assl.md).|  
|**Délai de requête**|Spécifie le temps (en secondes) après lequel une tentative de récupération des données expire.|  
|**Fournisseur managé**|Spécifie le nom du fournisseur managé. Si la connexion à la source de données utilise un fournisseur OLE DB natif, cette valeur est vide.|  
|**Informations d'emprunt d'identité**|Spécifie le compte d'emprunt d'identité utilisé pour les connexions de base de données lors du traitement ou de l'actualisation des données, les requêtes qui s'exécutent sur une banque de données relationnelle (via DirectQuery), les liaisons hors ligne, les partitions distantes et la synchronisation de la cible vers la source.<br /><br /> Les valeurs valides incluent le compte de service Analysis Services ou un jeu d'informations d'identification Windows spécifique. Ne spécifiez pas **Utiliser les infos d'identification de l'utilisateur actuel** ou **Hériter**. Ces options d'identification ne sont pas prises en charge pour une base de données model tabulaire.|  
  
  