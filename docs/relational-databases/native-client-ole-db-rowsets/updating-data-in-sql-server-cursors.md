---
title: Mise à jour des données dans les curseurs SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 788055ec21a215a99b2524310452d14ba390088a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300240"
---
# <a name="updating-data-in-sql-server-cursors"></a>Mise à jour des données dans les curseurs SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lors de la collecte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la mise à jour des données par l’intermédiaire de curseurs, une application de consommateur fournisseur de fournisseur OLE DB de native client est liée par les mêmes considérations et contraintes qui s’appliquent à toute autre application client.  
  
 Seules les lignes des curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] participent à un contrôle de simultanéité d'accès aux données. Lorsque le consommateur demande un ensemble de lignes modifiable, le contrôle de simultanéité est vérifié par DBPROP_LOCKMODE. Pour modifier le niveau de contrôle d'accès simultané, le consommateur définit la propriété DBPROP_LOCKMODE avant d'ouvrir l'ensemble de lignes.  
  
 Les niveaux d'isolation de la transaction peuvent provoquer des décalages significatifs dans la position des lignes si la conception de l'application cliente permet aux transactions de demeurer ouvertes sur une longue période de temps. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de DB OLE de client autochtone utilise le niveau d’isolement lu-engagé spécifié par DBPROPVAL_TI_READCOMMITTED. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB prend en charge l’isolement sale de lecture lorsque la concordance de ramset est lue seulement. Par conséquent, le consommateur peut demander un niveau supérieur d'isolation dans un ensemble de lignes modifiable, mais il ne peut pas demander avec succès un niveau inférieur.  
  
## <a name="immediate-and-delayed-update-modes"></a>Modes de mises à jour immédiat et différé  
 En mode de mise à jour immédiate, chaque appel à **IRowsetChange::SetData** entraîne un aller-retour vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le consommateur apporte plusieurs modifications à une seule ligne, il est plus efficace de soumettre toutes les modifications avec un seul appel à **SetData**.  
  
 En mode de mise à jour différée, un aller-retour vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a lieu pour chaque ligne indiquée dans les paramètres *cRows* et *rghRows* de **IRowsetUpdate::Update**.  
  
 Dans l'un et l'autre mode, un aller-retour représente une transaction distincte quand aucun objet de transaction n'est ouvert pour l'ensemble de lignes.  
  
 Lorsque vous utilisez **IRowsetUpdate::Mise à jour**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone essaie de traiter chaque rangée indiquée. Une erreur se produisant en raison des données, de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la longueur ou des valeurs de statut non valides pour n’importe quelle rangée n’empêche pas le traitement du fournisseur de DB OLE de client indigène. La totalité des autres lignes prenant part à la mise à jour peut être modifiée. Le consommateur doit examiner le tableau *de prgRowStatus* retourné [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour déterminer l’échec d’une rangée spécifique lorsque le fournisseur de DB OLE du client autochtone retourne DB_S_ERRORSOCCURRED.  
  
 Un consommateur ne doit pas présumer que les lignes sont traitées selon un ordre spécifique. Si un consommateur a besoin d'un traitement ordonné de la modification des données sur plusieurs lignes, le consommateur doit établir cet ordre dans la logique de l'application et ouvrir une transaction pour encadrer le processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des données dans les ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
