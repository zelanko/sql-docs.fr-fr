---
title: PDO::getAvailableDrivers
description: Référence API pour la fonction PDO::getAvailableDrivers dans le Pilote Microsoft PDO_SQLSRV pour PHP pour SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e43ef53820d24128d16ee0f0c7a5d6f1077ff6d2
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646619"
---
# <a name="pdogetavailabledrivers"></a>PDO::getAvailableDrivers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Retourne un tableau des pilotes PDO dans votre installation PHP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array PDO::getAvailableDrivers ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
Tableau avec la liste des pilotes PDO.  
  
## <a name="remarks"></a>Notes  
Le nom du pilote PDO est utilisé dans PDO::__construct pour créer une instance PDO.  
  
PDO::getAvailableDrivers n’est pas besoin d’être implémenté par les pilotes PHP. Pour plus d’informations sur cette méthode, consultez la documentation de PHP.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a> Exemple  
  
```  
<?php  
print_r(PDO::getAvailableDrivers());  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDO, classe](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
