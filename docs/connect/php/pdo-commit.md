---
title: PDO::Commit | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66808353b38742bf5327d02ca2a24d5f1fa1df3c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764867"
---
# <a name="pdocommit"></a>PDO::commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Envoie à la base de données des commandes qui ont été émises après l’appel à [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) , et rétablit la connexion en mode de validation automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDO::commit();  
```  
  
## <a name="return-value"></a>Valeur retournée  
La valeur est true si l’appel de méthode a réussi, false dans le cas contraire.  
  
## <a name="remarks"></a>Notes   
PDO::commit n’est pas affecté par (et n’affecte pas) la valeur de PDO::ATTR_AUTOCOMMIT.  
  
Consultez [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) pour obtenir un exemple qui utilise PDO::commit.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a> Voir aussi  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
