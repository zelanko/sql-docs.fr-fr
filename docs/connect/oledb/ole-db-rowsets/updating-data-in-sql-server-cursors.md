---
title: Mettre à jour les données dans les curseurs (pilote OLE DB)
description: Découvrez comment une application de contrôle serveur consommateur OLE DB Driver pour SQL Server fonctionne avec des requêtes dans un ensemble de lignes modifiable à l’aide de curseurs SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eae7b9119803615a2d18fe4710ff1eda2b91ac5b
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859929"
---
# <a name="updating-data-in-sql-server-cursors"></a>Mise à jour des données dans les curseurs SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Lorsque vous récupérez (fetch) et mettez à jour des données via des curseurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l’application de contrôle serveur consommateur OLE DB Driver pour SQL Server est liée par les mêmes contraintes que celles qui s’appliquent à toute autre application cliente.  
  
 Seules les lignes des curseurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participent à un contrôle de simultanéité d'accès aux données. Lorsque le consommateur demande un ensemble de lignes modifiable, le contrôle de simultanéité est vérifié par DBPROP_LOCKMODE. Pour modifier le niveau de contrôle d'accès simultané, le consommateur définit la propriété DBPROP_LOCKMODE avant d'ouvrir l'ensemble de lignes.  
  
 Les niveaux d'isolation de la transaction peuvent provoquer des décalages significatifs dans la position des lignes si la conception de l'application cliente permet aux transactions de demeurer ouvertes sur une longue période de temps. Par défaut, le pilote OLE DB pour SQL Server utilise le niveau d’isolation Lecture validée spécifié par DBPROPVAL_TI_READCOMMITTED. OLE DB Driver pour SQL Server prend en charge l'isolation de lecture erronée quand la concurrence d'ensembles de lignes est en lecture seule. Par conséquent, le consommateur peut demander un niveau supérieur d'isolation dans un ensemble de lignes modifiable, mais il ne peut pas demander avec succès un niveau inférieur.  
  
## <a name="immediate-and-delayed-update-modes"></a>Modes de mises à jour immédiat et différé  
 En mode de mise à jour immédiate, chaque appel à **IRowsetChange::SetData** entraîne un aller-retour vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si le consommateur apporte plusieurs modifications à une seule ligne, il est plus efficace de soumettre toutes les modifications avec un seul appel à **SetData**.  
  
 En mode de mise à jour différée, un aller-retour vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a lieu pour chaque ligne indiquée dans les paramètres *cRows* et *rghRows* de **IRowsetUpdate::Update**.  
  
 Dans l'un et l'autre mode, un aller-retour représente une transaction distincte quand aucun objet de transaction n'est ouvert pour l'ensemble de lignes.  
  
 Lorsque vous utilisez **IRowsetUpdate::Update**, OLE DB Driver pour SQL Server essaie de traiter chaque ligne indiquée. Une erreur liée à des données, des longueurs ou des valeurs d’état non valides n’interrompt pas le traitement du pilote OLE DB pour SQL Server. La totalité des autres lignes prenant part à la mise à jour peut être modifiée. Le consommateur doit examiner le tableau *prgRowStatus* retourné pour déterminer l’échec d’une ligne spécifique lorsque le pilote OLE DB pour SQL Server retourne DB_S_ERRORSOCCURRED.  
  
 Un consommateur ne doit pas présumer que les lignes sont traitées selon un ordre spécifique. Si un consommateur a besoin d'un traitement ordonné de la modification des données sur plusieurs lignes, le consommateur doit établir cet ordre dans la logique de l'application et ouvrir une transaction pour encadrer le processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des données dans les ensembles de lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
