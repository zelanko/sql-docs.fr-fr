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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a401cded16dc139e5efc70129ceb0d66fd68dcd6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923459"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Récupère la valeur d’un attribut PDOStatement prédéfini ou d’un attribut de pilote personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Paramètres  
$*attribute* : entier, une des constantes PDO::ATTR_* ou PDO::SQLSRV_ATTR_\*. Les attributs pris en charge sont ceux que vous pouvez définir avec [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), PDO::SQLSRV_ATTR_DIRECT_QUERY (pour plus d’informations, consultez [Exécution d’instruction directe et exécution d’instruction préparée dans le pilote PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO::ATTR_CURSOR et PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE (pour plus d’informations, consultez [Types de curseurs (pilote PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Valeur de retour  
En cas de réussite, retourne une valeur (mixte) pour un attribut PDO prédéfini ou un attribut de pilote personnalisé. En cas d’échec, retourne la valeur Null.  
  
## <a name="remarks"></a>Notes  
Pour obtenir un exemple, consultez [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
