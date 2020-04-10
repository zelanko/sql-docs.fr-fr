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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef4f53e4ee4ae1c9022ea8bfab0ba7a66c147c08
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922752"
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
  
