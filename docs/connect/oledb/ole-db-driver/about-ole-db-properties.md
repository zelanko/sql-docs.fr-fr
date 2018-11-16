---
title: À propos des propriétés OLE DB | Microsoft Docs
description: À propos des propriétés OLE DB
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- OLE DB Driver for SQL Server, properties
- properties [OLE DB]
- property values [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 903ce31cec6ce738fb478661da651f73a072e39d
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601529"
---
# <a name="about-ole-db-properties"></a>À propos des propriétés OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les consommateurs définissent des valeurs de propriétés afin de demander un comportement d'objet spécifique. Par exemple, ils utilisent des propriétés pour spécifier les interfaces à exposer par un ensemble de lignes. Ils obtiennent les valeurs de propriétés afin de déterminer les capacités d'un objet, tel qu'un ensemble de lignes, une session ou un objet source de données.  
  
 Chaque propriété a une valeur, un type, une description et un attribut de lecture/écriture et, pour les propriétés d'ensemble de lignes, un indicateur signalant s'il peut être appliqué sur la base de chaque colonne.  
  
 Une propriété est identifiée par un GUID et un entier représentant l'ID de propriété. Un jeu de propriétés est un jeu de toutes les propriétés qui partagent le même GUID. En plus des jeux de propriétés OLE DB prédéfinis, le pilote OLE DB pour SQL Server implémente des jeux de propriétés spécifiques au fournisseur et des propriétés dans ces jeux. Chaque propriété appartient à un ou plusieurs groupes de propriétés. Un groupe de propriétés est le groupe de toutes les propriétés qui s'appliquent à un objet particulier. Parmi les groupes de propriétés, on peut citer le groupe de propriétés d'initialisation, le groupe de propriétés de source de données, le groupe de propriétés de session, le groupe de propriétés d'ensemble de lignes, le groupe de propriétés de table et le groupe des propriétés de colonnes. Il y a des propriétés dans chacun de ces groupes de propriétés.  
  
 La définition de valeurs de propriétés implique les opérations suivantes  
  
1.  Détermination des propriétés pour lesquelles il faut définir des valeurs.  
  
2.  Détermination des jeux de propriétés qui contiennent les propriétés identifiées.  
  
3.  Allocation d'un tableau de structures DBPROPSET, une pour chaque jeu de propriétés identifié.  
  
4.  Allocation d'un tableau de structures DBPROP pour chaque jeu de propriétés. Le nombre d'éléments dans chaque tableau est le nombre de propriétés (identifiées à l'Étape 1) qui appartiennent à ce jeu de propriétés.  
  
5.  Remplissage de la structure DBPROP pour chaque propriété.  
  
6.  Remplissage des informations (GUID de jeu de propriétés, nombre d'éléments et un pointeur vers le tableau DBPROP correspondant) dans la structure DBPROPSET pour chaque jeu de propriétés.  
  
7.  Appel d'une méthode pour définir des propriétés et passer le nombre et le tableau de structures DBPROPSET.  
  
## <a name="see-also"></a> Voir aussi  
 [Création d’une application de pilote OLE DB pour SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [Propriétés (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
