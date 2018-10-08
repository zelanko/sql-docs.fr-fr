---
title: PDOStatement::getAttribute | Microsoft Docs
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17ef88f4dc899ce9108ff4a62cf4bc4bc7f8fabf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47738837"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Récupère la valeur d’un attribut PDOStatement prédéfini ou d’un attribut de pilote personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Paramètres  
$*attribute* : entier, une des constantes PDO::ATTR_* ou PDO::SQLSRV_ATTR_\*. Attributs pris en charge sont les attributs que vous pouvez définir avec [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), PDO::SQLSRV_ATTR_DIRECT_QUERY (pour plus d’informations, consultez [exécution d’instruction directe et exécution d’instruction préparée dans le pilote PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO::ATTR_CURSOR et PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE (pour plus d’informations, consultez [curseurs, Types (pilote PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Valeur retournée  
En cas de réussite, retourne une valeur (mixte) pour un attribut PDO prédéfini ou un attribut de pilote personnalisé. En cas d’échec, retourne la valeur Null.  
  
## <a name="remarks"></a>Notes   
Pour obtenir un exemple, consultez [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a> Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
