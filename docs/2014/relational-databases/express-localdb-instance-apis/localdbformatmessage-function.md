---
title: LocalDBFormatMessage fonction) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBFormatMessage
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 31b3152a-94cf-4f75-a31b-296d7dd16dbe
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d287a7ceff1c38c829da91a8ae2e530f664fb4ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63128740"
---
# <a name="localdbformatmessage-function"></a>Fonction LocalDBFormatMessage
  Retourne la description textuelle localisée pour l'erreur SQL Server Express LocalDB spécifiée.  
  
 **Fichier d’en-tête :** sqlncli. h  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LocalDBFormatMessage(  
           HRESULT hrLocalDB,  
           DWORD dwFlags,   
           DWORD dwLanguageId,   
           LPWSTR wszMessage,   
           LPDWORD lpcchMessage   
);  
```  
  
## <a name="parameters"></a>Paramètres  
 *hrLocalDB*  
 [Entrée] Code d'erreur de LocalDB.  
  
 *dwFlags*  
 [Entrée] Indicateurs spécifiant le comportement de cette fonction.  
  
 Indicateurs disponibles :  
  
 LOCALDB_TRUNCATE_ERR_MESSAGE  
 Si la mémoire tampon d'entrée est trop courte, le message d'erreur sera tronqué pour s'adapter à la mémoire tampon.  
  
 *dwLanguageId*  
 [Entrée] Langue souhaitée (LANGID) ou 0, auquel cas l'ordre du langage Win32 FormatMessage est utilisé.  
  
 *wszMessage*  
 [Sortie] Mémoire tampon pour stocker le message d'erreur de LocalDB.  
  
 *lpcchMessage*  
 [Entrée/sortie] En entrée contient la taille de la mémoire tampon de *wszMessage* en caractères. En sortie, si la taille de la mémoire tampon donnée est trop petite, contient la taille de la mémoire tampon requise en caractères, y compris les zéros de fin. Si la fonction réussit, contient le nombre de caractères du message, à l'exception des zéros de fin.  
  
## <a name="returns"></a>Retours  
 S_OK  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB n'est pas installé sur l'ordinateur.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Un ou plusieurs paramètres d'entrée spécifiés ne sont pas valides.  
  
 [LOCALDB_ERROR_UNKNOWN_ERROR_CODE](../express-localdb-error-messages/localdb-error-unknown-error-code.md)  
 Le message demandé n'existe pas.  
  
 [LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID](../express-localdb-error-messages/localdb-error-unknown-language-id.md)  
 Le message n'est pas disponible dans la langue demandée.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Le tampon d'entrée *wszMessage* est trop court, et la troncation n'est pas demandée.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s’est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="remarks"></a>Notes  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  
