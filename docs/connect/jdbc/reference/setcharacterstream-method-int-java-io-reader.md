---
title: Méthode setCharacterStream (int, java.io.Reader) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8004a4bda2cb68beb619db852dbef083d84c7d7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="setcharacterstream-method-int-javaioreader"></a>Méthode setCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné à l’objet java.io.Reader spécifié.  
  
> [!NOTE]  
>  Cette fonctionnalité a été introduite avec la [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] pilote JDBC version 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 Un **int** qui indique le nombre de paramètres.  
  
 *Lecteur*  
  
 L’objet java.io.Reader qui contient les données Unicode.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCharacterStream est spécifiée par la méthode setCharacterStream dans l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setCharacterStream &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
