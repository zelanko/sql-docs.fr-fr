---
title: Dossiers diagnostiques et champs Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- header records [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], diagnostic records
- ODBC error handling, diagnostic records
- SQLGetDiagField function
- diagnostic records [ODBC]
- errors [ODBC], diagnostic records
- fields [ODBC]
- status information [ODBC]
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b9cfea2db0ad0a5eadeede6df3f76ea3979243d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291799"
---
# <a name="diagnostic-records-and-fields"></a>Enregistrements et champs de diagnostic
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les enregistrements de diagnostic sont associés aux handles d'environnement, de connexion, d'instruction ou de descripteur ODBC. Lorsqu'une fonction ODBC déclenche un code de retour autre que SQL_SUCCESS ou SQL_INVALID_HANDLE, le handle appelé par la fonction est associé à des enregistrements de diagnostic qui contiennent des messages informationnels ou d'erreur. Ces enregistrements sont conservés jusqu'à ce qu'une autre fonction soit appelée à l'aide de ce handle, après quoi les enregistrements sont ignorés. Le nombre d'enregistrements de diagnostic pouvant être associés à un handle à un instant donné n'est pas limité.  
  
 Les enregistrements de diagnostic sont de deux types : en-tête et état. L'enregistrement d'en-tête est l'enregistrement 0 ; lorsque des enregistrements d'état sont présents, ils prennent les valeurs 1 et supérieures. Les enregistrements de diagnostic contiennent des champs différents pour l'enregistrement d'en-tête et les enregistrements d'état. Des composants ODBC peuvent également définir leurs propres champs d'enregistrement de diagnostic.  
  
 Les champs dans l'enregistrement d'en-tête contiennent des informations générales sur l'exécution d'une fonction, y compris le code de retour, le nombre de lignes, le nombre d'enregistrements d'état et le type d'instruction exécutée. L'enregistrement d'en-tête est toujours créé à moins qu'une fonction ODBC ne retourne SQL_INVALID_HANDLE. Pour une liste complète des champs dans l’enregistrement d’en-tête, voir [SQLGetDiagField](../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md).  
  
 Les champs dans les enregistrements d'état contiennent des informations sur des erreurs ou des avertissements spécifiques retournés par le gestionnaire de pilotes, le pilote ou la source de données ODBC, y compris la valeur SQLSTATE, le numéro d'erreur native, le message de diagnostic, le numéro de colonne et le numéro de ligne. Les enregistrements d'état sont créés uniquement si la fonction retourne SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA ou SQL_STILL_EXECUTING. Pour une liste complète des champs dans les registres d’état, voir **SQLGetDiagField**.  
  
 **SQLGetDiagRec** récupère un seul dossier diagnostique ainsi que son SQLSTATE ODBC, son numéro d’erreur autochtone et ses champs de messages diagnostiques. Cette fonctionnalité est similaire à l’ODBC 2. _x_**Fonction SQLError.** La fonction de manipulation d’erreur la plus simple dans ODBC 3. *x* est d’appeler à plusieurs reprises **SQLGetDiagRec** en commençant par le paramètre *RecNumber* réglé à 1 et incrémentant *RecNumber* par 1 jusqu’à ce que **SQLGetDiagRec** retourne SQL_NO_DATA. Cela équivaut à un ODBC 2. *x* application appelant **SQLError** jusqu’à ce qu’il revienne SQL_NO_DATA_FOUND.  
  
 ODBC 3. *x* prend en charge beaucoup plus d’informations diagnostiques que ODBC 2. *x*. Ces informations sont stockées dans d’autres champs dans des dossiers diagnostiques récupérés à l’aide **de SQLGetDiagField**.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC a des champs de diagnostic spécifiques au conducteur qui peuvent être récupérés avec **SQLGetDiagField**. Les étiquettes pour ces champs spécifiques au pilote sont définies dans sqlncli.h. Utilisez ces étiquettes pour récupérer l'état [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le niveau de gravité, le nom du serveur, le nom de la procédure et le numéro de ligne associés à chaque enregistrement de diagnostic. De plus, sqlncli.h contient des définitions des codes que le conducteur utilise pour identifier les relevés Transact-SQL si une application appelle **SQLGetDiagField** avec *DiagIdentifier* réglé pour SQL_DIAG_DYNAMIC_FUNCTION_CODE.  
  
 **SQLGetDiagField** est traité par le gestionnaire de pilote ODBC à l’aide d’informations d’erreur qu’il cache du conducteur sous-jacent. Le gestionnaire de pilotes ODBC ne met pas en cache les champs de diagnostic spécifiques aux pilotes tant qu'une connexion n'a pas été établie avec succès. **SQLGetDiagField** retourne SQL_ERROR s’il est appelé à obtenir des champs de diagnostic spécifiques au conducteur avant qu’une connexion réussie n’ait été conclue. Si une fonction de connexion ODBC retourne SQL_SUCCESS_WITH_INFO, les champs de diagnostic spécifiques au pilote pour la fonction de connexion ne sont pas encore disponibles. Vous pouvez commencer à appeler **SQLGetDiagField** pour les champs de diagnostic spécifiques au conducteur seulement après avoir fait un autre appel de fonction ODBC après la fonction de connexion.  
  
 La plupart des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erreurs signalées par le conducteur de l’ODBC du client autochtone peuvent être effectivement diagnostiquées en utilisant uniquement l’information retournée par **SQLGetDiagRec**. Toutefois, dans certains cas, les informations retournées par les champs de diagnostic spécifiques au pilote sont importantes pour diagnostiquer une erreur. Lorsque vous codez un gestionnaire d’erreur ODBC pour des applications utilisant le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote Native Client ODBC, il est une bonne idée d’utiliser également **SQLGetDiagField** pour récupérer au moins les SQL_DIAG_SS_MSGSTATE et SQL_DIAG_SS_SEVERITY champs spécifiques au conducteur. Si une erreur particulière peut être déclenchée à plusieurs endroits dans le code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SQL_DIAG_SS_MSGSTATE indique à un ingénieur du support technique Microsoft l'emplacement précis où une erreur a été déclenchée, ce qui peut parfois s'avérer utile pour diagnostiquer un problème.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
