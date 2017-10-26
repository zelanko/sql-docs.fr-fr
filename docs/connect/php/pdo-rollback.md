---
title: PDO::Rollback | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d918c1e3-1be0-4001-b3b0-000db6d9e8b8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6b0ef351838defa86dee7818727a0d538b3e071a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="pdorollback"></a>PDO::Rollback
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Supprime les commandes de base de données qui ont été émises après avoir appelé [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) et rétablit la connexion en mode de validation automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDO::rollBack ();  
```  
  
## <a name="return-value"></a>Valeur retournée  
La valeur est true si l’appel de méthode a réussi, false dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
PDO::ROLLBACK n’est pas affecté par (et n’affecte pas) la valeur de PDO::ATTR_AUTOCOMMIT.  
  
Consultez [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) pour obtenir un exemple qui utilise PDO::rollback.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[Classe PDO](../../connect/php/pdo-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

