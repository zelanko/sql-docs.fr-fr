---
title: sqlsrv_get_config | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f94c20c8aa6cf603c6588586e072813682b2ce68
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67992699"
---
# <a name="sqlsrv_get_config"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Retourne la valeur actuelle du paramètre de configuration spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>Paramètres  
*$setting*: paramètre de configuration pour lequel la valeur est retournée. Pour obtenir la liste des paramètres configurables, consultez [sqlsrv_configure](../../connect/php/sqlsrv-configure.md).  
  
## <a name="return-value"></a>Valeur de retour  
Valeur du paramètre spécifié par le paramètre *$setting* . Si un paramètre non valide est spécifié, **false** est retourné et une erreur est ajoutée à la collection d’erreurs.  
  
## <a name="remarks"></a>Notes  
Si **false** est retourné par **sqlsrv_get_config**, vous devez appeler [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) pour déterminer si une erreur s’est produite ou si **false** est la valeur du paramètre spécifié par le paramètre *$setting* .  
  
## <a name="see-also"></a>Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
