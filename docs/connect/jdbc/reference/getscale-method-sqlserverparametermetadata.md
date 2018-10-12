---
title: Méthode getScale (SQLServerParameterMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getScale
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b8d8d9c-74aa-4e6e-88f1-2fc5c74004ae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3de84426a1c15f45cebe5438e1ac877f32dc154e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718027"
---
# <a name="getscale-method-sqlserverparametermetadata"></a>Méthode getScale (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre de chiffres à droite de la virgule décimale pour le paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getScale(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *param*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Dans **int** qui indique l’échelle du paramètre désigné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getScale est spécifiée par la méthode getScale dans l’interface java.sql.ParameterMetaData.  
  
 Cette méthode obtient les chiffres de la colonne à droite de la virgule décimale. Pour les types qui n'ont pas de virgule décimale, cette méthode retourne la valeur « 0 ».  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerParameterMetaData, méthodes](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData, membres](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
