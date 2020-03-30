---
title: PDO::rollback | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d918c1e3-1be0-4001-b3b0-000db6d9e8b8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d37145856da6c4b3ff6def1620de443b20faebfb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67936198"
---
# <a name="pdorollback"></a>PDO::Rollback
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Supprime les commandes de base de données qui ont été émises après avoir appelé [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) et rétablit la connexion en mode de validation automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDO::rollBack ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
La valeur est true si l’appel de méthode a réussi, false dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
PDO::ROLLBACK n’est pas affecté par (et n’affecte pas) la valeur de PDO::ATTR_AUTOCOMMIT.  
  
Consultez [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) pour obtenir un exemple qui utilise PDO::rollback.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[PDO, classe](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
