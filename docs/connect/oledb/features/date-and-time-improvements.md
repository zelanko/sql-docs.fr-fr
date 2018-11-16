---
title: Améliorations date / heure | Microsoft Docs
description: Améliorations de date et d’heure dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: c7da4795d3485f5165ac7844f00d5a46f0a29cc9
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603666"
---
# <a name="date-and-time-improvements"></a>Améliorations des types de données date et heure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cette rubrique décrit le pilote OLE DB pour la prise en charge de SQL Server pour les types de données de date et d’heure qui ont été ajoutés dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
 Pour plus d’informations sur les améliorations de date/heure, consultez [améliorations Date / heure &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md).  
  
 Pour plus d’informations sur les exemples d’applications qui illustrent cette fonctionnalité, consultez [Exemples de programmation de données SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Utilisation  
 Les sections suivantes décrivent les différentes façons d'utiliser les nouveaux types de date et d'heure.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Utiliser le type Date comme type de données distinct  
 À partir de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], prise en charge améliorée pour les types date/heure rend plus efficace d’utiliser le type DBTYPE_DBDATE OLE DB.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Utiliser le type Time comme type de données distinct  
 OLE DB a déjà un type de données qui contient juste l'heure, DBTYPE_DBTIME, avec une précision de 1 seconde.
  
 Le nouveau type de données d’heure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a une précision en fractions de seconde de 100 nanosecondes. Cela nécessite un nouveau type dans OLE DB Driver pour SQL Server : DBTYPE_DBTIME2. Les applications existantes écrites pour utiliser des heures sans fractions de seconde peuvent recourir à des colonnes time(0). Le type OLE DB DBTYPE_TIME et ses structs correspondants doivent fonctionner correctement, à moins que les applications ne reposent sur le type retourné dans les métadonnées.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Utiliser le type Time comme type de données distinct avec l'extension de la précision en fractions de seconde  
 Certaines applications, telles que les applications de contrôle de processus et de fabrication, requièrent la possibilité de gérer les données d'heure avec une précision allant jusqu'à 100 nanosecondes. Nouveau type à cet effet dans OLE DB est DBTYPE_DBTIME2.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Utiliser le type Datetime avec l'extension de la précision en fractions de seconde  
 OLE DB définit déjà un type avec une précision allant jusqu'à 1 nanoseconde. Toutefois, ce type est déjà utilisé par les applications [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] existantes, lesquelles attendent une précision de 1/300 de seconde uniquement. Le nouveau type **datetime2(3)** n’est pas directement compatible avec le type datetime existant. S'il existe un risque que cela affecte le comportement des applications, celles-ci doivent utiliser un nouvel indicateur DBCOLUMN pour déterminer le type réel sur le serveur.    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Utiliser le type Datetime avec l'extension de la précision en fractions de seconde et le fuseau horaire  
 Certaines applications requièrent des valeurs datetime avec les informations de fuseau horaire. Cela est pris en charge par le nouveau type DBTYPE_DBTIMESTAMPOFFSET.
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Utiliser les données de type Date/Time/Datetime/Datetimeoffset avec des conversions côté client cohérentes avec les conversions existantes  
 Les conversions sont étendues de manière cohérente afin d’inclure celles entre tous les types relatifs à la date et à l’heure introduits dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
