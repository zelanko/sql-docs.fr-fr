---
title: Méthode getResponseBuffering (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getResponseBuffering()
apilocation:
- SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4b3e53579b8c95cce0585e9614152053f39cafa8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980433"
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>Méthode getResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le mode de mise en mémoire tampon des réponses pour cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant une minuscule, **full** ou **adaptative**.  
  
## <a name="remarks"></a>Notes  
 La valeur **full** consiste à lire l’intégralité du résultat du serveur à l’exécution.  
  
 La valeur **adaptive** consiste à mettre en mémoire tampon le moins de données possible si nécessaire. La valeur **adaptive** correspond au mode de mise en mémoire tampon par défaut.  
  
 Pour plus d’informations sur le mode de mise en mémoire tampon des réponses, consultez [Utiliser la mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Voir aussi  
 [setResponseBuffering, méthode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
