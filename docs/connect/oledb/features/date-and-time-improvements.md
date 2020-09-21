---
title: Améliorations des types de données de date et d’heure | Microsoft Docs
description: Découvrez comment OLE DB Driver pour SQL Server prend en charge des types de données de date et d'heure ajoutés à SQL Server 2008.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba77a851ca8193ab3f809352d0d7804cc8189f6c
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861494"
---
# <a name="date-and-time-improvements"></a>Améliorations des types de données date et heure
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cette rubrique décrit la prise en charge par OLE DB Driver pour SQL Server des types de données de date et d'heure ajoutés à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
 Pour plus d'informations sur les améliorations apportées en matière de date et d'heure, consultez [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md).  
  
 Pour plus d’informations sur les exemples d’applications qui illustrent cette fonctionnalité, consultez [Exemples de programmation de données SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Usage  
 Les sections suivantes décrivent les différentes façons d'utiliser les nouveaux types de date et d'heure.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Utiliser le type Date comme type de données distinct  
 À partir de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], l'amélioration de la prise en charge des types date/heure rend plus efficace l'utilisation du type DBTYPE_DBDATE OLE DB.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Utiliser le type Time comme type de données distinct  
 OLE DB a déjà un type de données qui contient juste l'heure, DBTYPE_DBTIME, avec une précision de 1 seconde.
  
 Le nouveau type de données d’heure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a une précision en fractions de seconde de 100 nanosecondes. Cela nécessite un nouveau type dans OLE DB Driver pour SQL Server : DBTYPE_DBTIME2. Les applications existantes écrites pour utiliser des heures sans fractions de seconde peuvent recourir à des colonnes time(0). Le type OLE DB DBTYPE_TIME et ses structs correspondants doivent fonctionner correctement, à moins que les applications ne reposent sur le type retourné dans les métadonnées.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Utiliser le type Time comme type de données distinct avec l'extension de la précision en fractions de seconde  
 Certaines applications, telles que les applications de contrôle de processus et de fabrication, requièrent la possibilité de gérer les données d'heure avec une précision allant jusqu'à 100 nanosecondes. Dans OLE DB, le nouveau type est DBTYPE_DBTIME2.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Utiliser le type Datetime avec l'extension de la précision en fractions de seconde  
 OLE DB définit déjà un type avec une précision allant jusqu'à 1 nanoseconde. Toutefois, ce type est déjà utilisé par les applications [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] existantes, lesquelles attendent une précision de 1/300 de seconde uniquement. Le nouveau type **datetime2(3)** n’est pas directement compatible avec le type datetime existant. S'il existe un risque que cela affecte le comportement des applications, celles-ci doivent utiliser un nouvel indicateur DBCOLUMN pour déterminer le type réel sur le serveur.    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Utiliser le type Datetime avec l'extension de la précision en fractions de seconde et le fuseau horaire  
 Certaines applications requièrent des valeurs datetime avec les informations de fuseau horaire. Cela est pris en charge par le nouveau type DBTYPE_DBTIMESTAMPOFFSET.
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Utiliser les données de type Date/Time/Datetime/Datetimeoffset avec des conversions côté client cohérentes avec les conversions existantes  
 Les conversions sont étendues de manière cohérente afin d’inclure celles entre tous les types relatifs à la date et à l’heure introduits dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
