---
title: Méthode isWrapperFor (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53f3291f-d43a-476b-a656-d86168dacf6c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e98b901663a63b353e14ae31308e244a55a78369
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80915119"
---
# <a name="iswrapperfor-method-sqlserverstatement"></a>Méthode isWrapperFor (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cet objet d'instruction est un wrapper pour l'interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *iface*  
  
 **Classe** définissant une interface.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si cet objet implémente l’interface ou encapsule un objet qui l’implémente. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Les méthodes [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) et [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) sont définies par l’interface java.sql.Wrapper, introduite dans JDBC 4.0.  
  
 Si cette méthode retourne la valeur True, l’appel de [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) avec le même argument réussit.  
  
 Pour un exemple de code, voir [Exemple de mise à jour de données volumineuses](../../../connect/jdbc/updating-large-data-sample.md).  
  
 Pour plus d’informations, consultez [Wrappers et interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode unwrap &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
