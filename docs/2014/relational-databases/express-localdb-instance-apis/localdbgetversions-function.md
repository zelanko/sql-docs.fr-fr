---
title: Fonction LocalDBGetVersions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersions
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 033a9c6b-0d7f-4f8a-ab60-33cd6fee0d33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 431124cff2fcf293ccf1e8e8bcb74321245a661e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63032282"
---
# <a name="localdbgetversions-function"></a>Fonction LocalDBGetVersions
  Retourne toutes les versions de SQL Server Express LocalDB disponibles sur l'ordinateur.  
  
 **Fichier d'en-tête :** sqlncli.h  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#define MAX_LOCALDB_VERSION_LENGTH 43typedef WCHAR TLocalDBVersion[MAX_LOCALDB_VERSION_LENGTH + 1];typedef TLocalDBVersion* PTLocalDBVersion;HRESULT LocalDBGetVersions(           PTLocalDBVersion pVersion,           LPDWORD lpdwNumberOfVersions);  
```  
  
## <a name="parameters"></a>Paramètres  
 *pVersionNames*  
 [Sortie] Contient les noms des versions de base de données locale qui sont disponibles sur le poste de travail.  
  
 *lpdwNumberOfVersions*  
 [Entrée/sortie] En entrée, contient le nombre d'emplacements de versions dans la mémoire tampon de *pVersionNames* .   
En sortie, contient le nombre de versions de LocalDB existantes.  
  
## <a name="returns"></a>Valeur renvoyée  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB n'est pas installé sur l'ordinateur.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Un ou plusieurs paramètres d'entrée spécifiés ne sont pas valides.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Le tampon d'entrée est trop court, et la troncation n'a pas été demandée.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s'est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="remarks"></a>Notes  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version de la base de données locale SQL Server Express](sql-server-express-localdb-header-and-version-information.md)  
  
  
