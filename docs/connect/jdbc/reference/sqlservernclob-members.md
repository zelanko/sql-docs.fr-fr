---
title: Membres de SQLServerNClob | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80f495051aabf5ecf3d020fc749cfdb4ddfd4c5f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923536"
---
# <a name="sqlservernclob-members"></a>Membres de SQLServerNClob
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Les tableaux suivants présentent les membres exposés par la classe [SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md).  
  
## <a name="constructors"></a>Constructeurs  
 Aucun.  
  
## <a name="fields"></a>Champs  
 Aucun.  
  
## <a name="inherited-fields"></a>Champs hérités  
 Aucun.  
  
## <a name="methods"></a>Méthodes  
  
|Name|Description|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|Cette méthode libère l’objet **NCLOB** ainsi que les ressources qu’il détient.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|Récupère la valeur **NCLOB** désignée par l’objet **java.sql.NClob** sous forme de flux ASCII.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|Récupère la valeur **NCLOB** désignée par l’objet **java.sql.NClob**.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|Récupère une copie de la sous-chaîne spécifiée dans la valeur **NCLOB** désignée par l’objet **java.sql.NClob**.|  
|[length](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|Récupère le nombre de caractères de la valeur **NCLOB** désignée par l’objet **java.sql.NClob**.|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|Récupère la position de caractère de l’objet **java.sql.NClob** spécifié ou d’une sous-chaîne du **java.sql.NClob** en fonction de la position de départ spécifiée.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|Récupère un flux servant à écrire des caractères ASCII dans la valeur **NCLOB** représentée par cet objet **java.sql.NClob**, en commençant à la position spécifiée.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|Récupère un flux servant à écrire un flux de caractères Unicode dans la valeur **NCLOB** représentée par cet objet **java.sql.NClob**, en commençant à la position spécifiée.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|Écrit la **chaîne** spécifiée dans le **NCLOB**, en démarrant à la position spécifiée.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|Tronque la valeur **NCLOB** en fonction de la longueur spécifiée.|  
  
## <a name="inherited-methods"></a>Méthodes héritées  
  
|Classe héritée de|Méthodes|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
