---
title: La mise à jour des données dans les curseurs SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caa3f5d35d51a90809175da88c9732fd883d291d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428328"
---
# <a name="updating-data-in-sql-server-cursors"></a>Mise à jour des données dans les curseurs SQL Server
  Lors de l’extraction et la mise à jour des données via [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseurs, un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] application consommateur de fournisseur OLE DB Native Client est liée par les mêmes considérations et contraintes qui s’appliquent à n’importe quel autre application cliente.  
  
 Seules les lignes des curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] participent à un contrôle de simultanéité d'accès aux données. Lorsque le consommateur demande un ensemble de lignes modifiable, le contrôle de simultanéité est vérifié par DBPROP_LOCKMODE. Pour modifier le niveau de contrôle d'accès simultané, le consommateur définit la propriété DBPROP_LOCKMODE avant d'ouvrir l'ensemble de lignes.  
  
 Les niveaux d'isolation de la transaction peuvent provoquer des décalages significatifs dans la position des lignes si la conception de l'application cliente permet aux transactions de demeurer ouvertes sur une longue période de temps. Par défaut, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fournisseur OLE DB utilise le niveau d’isolation de lecture validée spécifié par DBPROPVAL_TI_READCOMMITTED. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge l’isolation de lecture erronée lors de la concurrence de l’ensemble de lignes est en lecture seule. Par conséquent, le consommateur peut demander un niveau supérieur d'isolation dans un ensemble de lignes modifiable, mais il ne peut pas demander avec succès un niveau inférieur.  
  
## <a name="immediate-and-delayed-update-modes"></a>Modes de mises à jour immédiat et différé  
 En mode de mise à jour immédiate, chaque appel à **IRowsetChange::SetData** provoque un aller-retour vers le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le consommateur apporte plusieurs modifications à une seule ligne, il est plus efficace de soumettre toutes les modifications avec un seul **SetData** appeler.  
  
 En mode de mise à jour différée, un aller-retour vers le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour chaque ligne indiquée dans le *cRows* et *rghRows* paramètres de **IRowsetUpdate::Update**.  
  
 Dans l'un et l'autre mode, un aller-retour représente une transaction distincte quand aucun objet de transaction n'est ouvert pour l'ensemble de lignes.  
  
 Lorsque vous utilisez **IRowsetUpdate::Update**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif essaie de traiter chaque ligne indiquée. Une erreur se produit en raison de valeurs de données, longueur ou l’état non valides pour n’importe quelle ligne ne s’arrête pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traitement du fournisseur OLE DB Native Client. La totalité des autres lignes prenant part à la mise à jour peut être modifiée. Le consommateur doit examiner le *prgRowStatus* tableau pour déterminer l’échec pour n’importe quel spécifique ligne lorsque la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client retourne DB_S_ERRORSOCCURRED.  
  
 Un consommateur ne doit pas présumer que les lignes sont traitées selon un ordre spécifique. Si un consommateur a besoin d'un traitement ordonné de la modification des données sur plusieurs lignes, le consommateur doit établir cet ordre dans la logique de l'application et ouvrir une transaction pour encadrer le processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des données dans les ensembles de lignes](updating-data-in-rowsets.md)  
  
  
