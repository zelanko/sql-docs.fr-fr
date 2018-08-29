---
title: Mise à jour d’une application à partir de SQL Server 2005 Native Client | Microsoft Docs
description: Mise à jour d’une application à partir de SQL Server 2005 Native Client
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 15d4f01dbf35385e1fba296e5d78e57fa35f16ed
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034891"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Mise à jour d'une application depuis SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cette rubrique décrit les modifications avec rupture dans OLE DB Driver pour SQL Server depuis [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

 Quand vous effectuez une mise à niveau de MDAC (Microsoft Data Access Components) vers OLE DB Driver pour SQL Server, vous pouvez également constater des différences de comportement. Pour plus d’informations, consultez [mise à jour d’une Application vers OLE DB Driver pour SQL Server à partir de MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 livré avec [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 livré avec [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 livré avec [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 livré avec [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  

|Modifié le comportement dans OLE DB Driver pour SQL Server par rapport à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB effectue un remplissage uniquement à l'échelle définie.|Pour les conversions où les données sont envoyées au serveur, OLE DB Driver pour SQL Server remplit les zéros de fin dans les données uniquement jusqu'à la longueur maximale de **datetime** valeurs. SQL Server Native Client 9.0 effectuaient un remplissage à neuf chiffres.|  
|Valider DBTYPE_DBTIMESTAMP pour ICommandWithParameter::SetParameterInfo.|OLE DB Driver pour SQL Server implémente la spécification OLE DB pour *bScale* dans ICommandWithParameter::SetParameterInfo doit être défini à la précision de fractions pour DBTYPE_DBTIMESTAMP.|  
|Le **sp_columns** procédure stockée maintenant renvoie **« Non »** au lieu de **« Non »** pour la colonne IS_NULLABLE.|Dans OLE DB Driver pour SQL Server, **sp_columns** procédure stockée maintenant renvoie **« Non »** au lieu de **« Non »** pour une colonne IS_NULLABLE.|  
|Erreur différente retournée lorsque la date est hors limites.|Pour le **datetime** type, un numéro d’erreur différent est retourné par le pilote OLE DB pour SQL Server pour une date hors des limites que vous a été retourné dans les versions antérieures.<br /><br /> Plus précisément, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 retournait l’erreur 22007 pour toutes les valeurs hors limites année lors des conversions de chaîne à **datetime**, et OLE DB Driver pour SQL Server retourne l’erreur 22008 lorsque la date est comprise dans la plage prise en charge par **datetime2** mais en dehors de la plage prise en charge par **datetime** ou **smalldatetime**.|  
|La valeur **datetime** tronque les fractions de seconde et n’arrondit pas si cela entraîne une modification du jour.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, le comportement client pour les valeurs **datetime** envoyées au serveur consistait à les arrondir au 1/300e de seconde. Dans OLE DB Driver pour SQL Server, ce scénario provoque une troncation des fractions de seconde si l’arrondi modifie le jour.|  
|Possible troncation de secondes pour **datetime** valeur.|Une application générée avec OLE DB Driver pour SQL Server qui se connecte à un serveur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 tronquera des secondes et des fractions de seconde pour la partie heure des données envoyées au serveur si vous créez une liaison avec une colonne datetime à l’aide d’un identificateur de type DBTYPE_DBTIMESTAMP (OLE DB) ou SQL_TIMESTAMP (ODBC) et d’une échelle égale à 0.<br /><br /> Exemple :<br /><br /> Données d'entrée : 1994-08-21 21:21:36.000<br /><br /> Données insérées : 1994-08-21 21:21:00.000|  
|La conversion de données OLE DB de DBTYPE_DBTIME vers DBTYPE_DATE ne peut plus provoquer de changement de jour.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, si la partie heure d'un DBTYPE_DATE était à moins d'une demi-seconde de minuit, le code de conversion OLE DB provoquait le changement de jour. Dans OLE DB Driver pour SQL Server, le jour ne change pas (en fractions de seconde est tronquées et non arrondies).|  
|Modifications de conversion IBCPSession::BCColFmt.|Dans OLE DB Driver pour SQL Server, lorsque vous utilisez IBCPSession::BCOColFmt pour convertir SQLDATETIME ou SQLDATETIME en un type chaîne, une valeur fractionnaire est exportée. Par exemple, lors de la conversion du type SQLDATETIME en type SQLNVARCHARMAX, les versions antérieures à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 retournaient<br /> 1989-02-01 00:00:00.<br />OLE DB Driver pour SQL Server retourne <br />1989-02-01 00:00:00.0000000.|  
|Les applications personnalisées qui utilisent l'API BCP peuvent maintenant afficher un avertissement.|L'API BCP génère un message d'avertissement si la longueur des données est supérieure à la longueur spécifiée pour un champ pour tous les types. Auparavant, cet avertissement était affiché uniquement pour les types caractère, et non pour tous les types.|  
|L’insertion d’une chaîne vide dans un **sql_variant** lié en tant que type date/heure génère une erreur.|Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0, l’insertion d’une chaîne vide dans un **sql_variant** lié en tant que type date/heure ne générait pas d’erreur. OLE DB Driver pour SQL Server génère correctement une erreur dans cette situation.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut retourner des résultats différents lorsque le déclencheur s’exécute.|Des modifications apportées dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ont pu amener une application à avoir des résultats différents retournés par une instruction, ce qui a entraîné l’exécution d’un déclencheur quand **NOCOUNT OFF** était actif. Dans ce cas, votre application peut générer une erreur. Pour résoudre cette erreur, définissez **NOCOUNT ON** dans le déclencheur.|  

## <a name="see-also"></a> Voir aussi   
 [OLE DB Driver pour SQL Server](../../oledb/oledb-driver-for-sql-server.md)
