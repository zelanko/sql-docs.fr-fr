---
title: Les membres de SQLServerParameterMetaData | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f9ebb203-2013-4feb-94f5-494b7f098f9a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: abd82d1a5da6e64962ee10edac0e3ad4ed2db0eb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621807"
---
# <a name="sqlserverparametermetadata-members"></a>Membres de SQLServerParameterMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Les tableaux suivants présentent les membres exposés par la classe [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md).  
  
## <a name="constructors"></a>Constructeurs  
 Aucun.  
  
## <a name="fields"></a>Champs  
 Aucun.  
  
## <a name="inherited-fields"></a>Champs hérités  
  
|Nom   |Description|  
|----------|-----------------|  
|java.sql.ParameterMetaData|parameterModeIn, parameterModeInOut, parameterModeOut, parameterModeUnknown, parameterNoNulls, parameterNullable, parameterNullableUnknown|  
  
## <a name="methods"></a>Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|[getParameterClassName](../../../connect/jdbc/reference/getparameterclassname-method-sqlserverparametermetadata.md)|Récupère le nom complet de la classe Java dont les instances doivent être transmises à la méthode [setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) de la classe [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).|  
|[getParameterCount](../../../connect/jdbc/reference/getparametercount-method-sqlserverparametermetadata.md)|Récupère le nombre de paramètres dans l’objet [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) pour lesquels cet objet [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) contient des informations.|  
|[getParameterMode](../../../connect/jdbc/reference/getparametermode-method-sqlserverparametermetadata.md)|Récupère le mode du paramètre désigné.|  
|[getParameterType](../../../connect/jdbc/reference/getparametertype-method-sqlserverparametermetadata.md)|Récupère le type SQL du paramètre désigné.|  
|[getParameterTypeName](../../../connect/jdbc/reference/getparametertypename-method-sqlserverparametermetadata.md)|Récupère le nom de type spécifique à la base de données du paramètre désigné.|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverparametermetadata.md)|Récupère le nombre de décimales pour le paramètre désigné.|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverparametermetadata.md)|Récupère le nombre de chiffres à droite de la virgule décimale pour le paramètre désigné.|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverparametermetadata.md)|Récupère les informations déterminant si les valeurs Null sont autorisées dans le paramètre désigné.|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverparametermetadata.md)|Récupère les informations déterminant si les valeurs pour le paramètre désigné peuvent être des nombres signés.|  
  
## <a name="inherited-methods"></a>Méthodes héritées  
  
|Classe héritée de :|Méthodes|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
