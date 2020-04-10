---
title: Méthode getTrustStore (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 43b537a20cf39d64e06baf6f0cae78ed46526915
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80911156"
---
# <a name="gettruststore-method-sqlserverdatasource"></a>Méthode getTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le chemin d'accès (y compris le nom de fichier) au fichier trustStore de certificat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **String** contenant le chemin (y compris le nom de fichier) du fichier trustStore de certificat, ou Null si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Si la propriété trustStore n’est pas définie, la méthode [getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) retourne la valeur Null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
