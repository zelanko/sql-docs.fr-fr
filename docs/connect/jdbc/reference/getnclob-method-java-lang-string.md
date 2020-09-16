---
description: Méthode getNClob (java.lang.String)
title: Méthode getNClob (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: be01ce56-8f13-437b-8de6-246cda5f7830
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 031ca2e70d3b5ffb561a6f8ef67de89ab7889644
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435281"
---
# <a name="getnclob-method-javalangstring"></a>Méthode getNClob (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur d’un paramètre **NCLOB** JDBC sous forme d’objet NClob dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.NClob getNClob(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet NClob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNClob est spécifiée par la méthode getNClob de l’interface java.sql.CallableStatement.  
  
 Cette méthode ne permet de récupérer que des paramètres **NCHAR**, **NVARCHAR**, **NTEXT** et **XML**. L'appel de ces méthodes sur d'autres paramètres de type de données entraîne une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [getNClob, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
