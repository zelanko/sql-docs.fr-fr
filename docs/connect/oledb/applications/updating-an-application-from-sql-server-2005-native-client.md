---
title: Mise à jour d’une application à partir de SQL Server 2005 Native Client | Microsoft Docs
description: Mise à jour d’une application à partir de SQL Server 2005 Native Client
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7915b9fb74f05057e05eef022d7f9b0e4ccdd21f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989250"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Mise à jour d'une application depuis SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cette rubrique décrit les dernières modifications apportées à OLE DB pilote pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL Server depuis native [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]client dans.  

 Quand vous effectuez une mise à niveau de MDAC (Microsoft Data Access Components) vers OLE DB Driver pour SQL Server, vous pouvez également constater des différences de comportement. Pour plus d’informations, consultez [mise à jour d’une application vers OLE DB pilote pour SQL Server à partir de MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 livré avec [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 livré avec [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 livré avec [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 livré avec [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  

|Comportement modifié dans OLE DB pilote pour SQL Server comparé à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB effectue un remplissage uniquement à l'échelle définie.|Pour les conversions où les données converties sont envoyées au serveur, OLE DB pilote pour SQL Server remplit les zéros à droite dans les données uniquement jusqu’à la longueur maximale des valeurs **DateTime** . SQL Server Native Client 9.0 effectuaient un remplissage à neuf chiffres.|  
|Validez DBTYPE_DBTIMESTAMP pour ICommandWithParameter:: SetParameterInfo.|OLE DB pilote pour SQL Server implémente la spécification de OLE DB pour *bScale* dans ICommandWithParameter:: SetParameterInfo à définir sur la précision en fractions de seconde pour DBTYPE_DBTIMESTAMP.|  
|La procédure stockée **sp_columns** retourne à présent **«no»** au lieu de **«no»** pour la colonne IS_NULLABLE.|Dans OLE DB pilote pour SQL Server, la procédure stockée **sp_columns** retourne désormais la valeur **«non»** au lieu de **«non»** pour une colonne IS_NULLABLE.|  
|Erreur différente retournée lorsque la date est hors limites.|Pour le type **DateTime** , un numéro d’erreur différent est retourné par OLE DB pilote pour SQL Server pour une date hors limites que celle qui a été retournée dans les versions antérieures.<br /><br /> Plus précisément [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Native Client 9,0 a renvoyé 22007 pour toutes les valeurs hors limites de l’année dans les conversions de chaînes en **DateTime**et OLE DB pilote pour SQL Server retourne 22008 lorsque la date est dans la plage prise en charge par **datetime2** , mais en dehors plage prise en charge par **DateTime** ou **smalldatetime**.|  
|La valeur **datetime** tronque les fractions de seconde et n’arrondit pas si cela entraîne une modification du jour.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, le comportement client pour les valeurs **datetime** envoyées au serveur consistait à les arrondir au 1/300e de seconde. Dans OLE DB pilote pour SQL Server, ce scénario provoque une troncation des fractions de seconde si l’arrondi modifie le jour.|  
|Trunction possibles de secondes pour la valeur **DateTime** .|Une application générée avec OLE DB Driver pour SQL Server qui se connecte à un serveur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 tronquera des secondes et des fractions de seconde pour la partie heure des données envoyées au serveur si vous créez une liaison avec une colonne datetime à l’aide d’un identificateur de type DBTYPE_DBTIMESTAMP (OLE DB) ou SQL_TIMESTAMP (ODBC) et d’une échelle égale à 0.<br /><br /> Par exemple :<br /><br /> Données d'entrée : 1994-08-21 21:21:36.000<br /><br /> Données insérées : 1994-08-21 21:21:00.000|  
|La conversion de données OLE DB de DBTYPE_DBTIME vers DBTYPE_DATE ne peut plus provoquer de changement de jour.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, si la partie heure d'un DBTYPE_DATE était à moins d'une demi-seconde de minuit, le code de conversion OLE DB provoquait le changement de jour. Dans OLE DB pilote pour SQL Server, le jour ne change pas (les fractions de seconde sont tronquées et non arrondies).|  
|IBCPSession:: BCColFmt conversion des modifications.|Dans OLE DB pilote pour SQL Server, quand vous utilisez IBCPSession:: BCOColFmt pour convertir SQLDATETIME ou SQLDATETIME en un type chaîne, une valeur fractionnaire est exportée. Par exemple, lors de la conversion du type SQLDATETIME en type SQLNVARCHARMAX, les versions antérieures à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 retournaient<br /> 1989-02-01 00:00:00.<br />OLE DB Driver pour SQL Server retourne <br />1989-02-01 00:00:00.0000000.|  
|Les applications personnalisées qui utilisent l'API BCP peuvent maintenant afficher un avertissement.|L'API BCP génère un message d'avertissement si la longueur des données est supérieure à la longueur spécifiée pour un champ pour tous les types. Auparavant, cet avertissement était affiché uniquement pour les types caractère, et non pour tous les types.|  
|L’insertion d’une chaîne vide dans un **sql_variant** lié en tant que type date/heure génère une erreur.|Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0, l’insertion d’une chaîne vide dans un **sql_variant** lié en tant que type date/heure ne générait pas d’erreur. OLE DB pilote pour SQL Server génère correctement une erreur dans cette situation.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut retourner des résultats différents lorsque le déclencheur s’exécute.|Des modifications apportées dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ont pu amener une application à avoir des résultats différents retournés par une instruction, ce qui a entraîné l’exécution d’un déclencheur quand **NOCOUNT OFF** était actif. Dans ce cas, votre application peut générer une erreur. Pour résoudre cette erreur, définissez **NOCOUNT on** dans le déclencheur.|  

## <a name="see-also"></a>Voir aussi   
 [OLE DB Driver pour SQL Server](../../oledb/oledb-driver-for-sql-server.md)
