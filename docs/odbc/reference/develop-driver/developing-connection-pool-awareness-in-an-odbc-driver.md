---
title: Développement de la reconnaissance des pools de connexion dans un pilote ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b82e56dd7998ca19ce9e401369cd8d2f52b58573
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62636223"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Développement de la reconnaissance des pools de connexions dans un pilote ODBC
Cette rubrique décrit les détails du développement d’un pilote ODBC qui contient des informations sur la façon dont le pilote doit fournir des services de regroupement de connexion.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Activer le regroupement de connexions prenant en charge de pilote  
 Un pilote doit implémenter les fonctions d’Interface de fournisseur de Service ODBC (SPI) suivantes :  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 Consultez [référence de l’Interface de fournisseur de Service ODBC (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) pour plus d’informations.  
  
 Un pilote doit également implémenter les fonctions existantes suivantes afin que le pilote prenant en charge le regroupement peut être activé :  
  
|Fonction|Fonctionnalités supplémentaires|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Prise en charge le nouveau type de handle : SQL_HANDLE_DBC_INFO_TOKEN (voir la description ci-dessous).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Prise en charge le nouvel attribut de connexion uniquement : SQL_ATTR_DBC_INFO_TOKEN permettant de réinitialiser la connexion (voir la description ci-dessous).|  
  
> [!NOTE]  
>  Fonctions déconseillées comme **SQLError** et **SQLSetConnectOption** ne sont pas pris en charge pour le regroupement de connexions prenant en charge de pilote.  
  
## <a name="the-pool-id"></a>L’ID du Pool  
 L’ID du pool est un ID de spécifiques au pilote de longueur de pointeur pour représenter un groupe particulier de connexions qui peuvent être utilisés indifféremment. Étant donné un ensemble d’informations de connexion, un pilote doit pouvoir rapidement déduire l’ID de pool correspondant.  
  
 Par exemple, l’ID du pool doit encoder les informations de nom et les informations d’identification du serveur. Toutefois, le nom de la base de données n’est pas nécessaire, car un pilote peut être en mesure de réutiliser une connexion, puis modifier la base de données dans moins de temps que la création d’une nouvelle connexion.  
  
 Un pilote doit définir un ensemble d’attributs de clé, qui constitueront l’ID de pool. La valeur de ces attributs clés peut provenir des attributs de connexion, de chaîne de connexion et de source de données. Dans le cas où il existe des conflits de ces sources, la stratégie de résolution existant, spécifiques au pilote doit être utilisée pour la compatibilité descendante.  
  
 Le Gestionnaire de pilotes utilise un autre pool pour différents ID de pool. Toutes les connexions dans le même pool sont réutilisables. Le Gestionnaire de pilotes ne seront jamais réutiliser une connexion avec un ID de pool différent.  
  
 Par conséquent pilotes doivent affecter un ID de pool unique pour chaque groupe de connexions avec la même valeur dans leurs attributs de clé définies. Si un pilote utilise le même ID de pool pour les deux connexions avec des valeurs différentes dans leurs attributs de clé, le Gestionnaire de pilotes seront toujours placez-les dans le même pool (le Gestionnaire de pilotes ne sait rien sur les attributs de clé spécifiques au pilote). Cela signifie que le pilote a besoin signaler au Gestionnaire de pilote qui n’est pas réutilisable à l’intérieur d’une connexion avec un autre ensemble d’attributs clés [sqlrateconnection, fonction](../../../odbc/reference/syntax/sqlrateconnection-function.md). Cela peut réduire les performances, et cela n’est pas recommandé.  
  
 Le Gestionnaire de pilotes réutilise pas une connexion allouée à partir d’un autre environnement de pilote, même si toutes les informations de connexion correspond à. Le Gestionnaire de pilotes est destiné à un autre pool autre environnement, même lorsque les connexions ont le même ID de pool. Par conséquent, l’ID du pool est propre à son environnement pilote.  
  
 La fonction permettant d’obtenir l’ID du pool à partir du pilote est [sqlgetpoolid, fonction](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>L’évaluation de la connexion  
 Par rapport à l’établissement d’une nouvelle connexion, vous pouvez obtenir de meilleures performances en réinitialisant certaines informations de connexion (par exemple, la base de données) dans une connexion regroupée. Par conséquent, vous souhaiterez peut-être pas le nom de base de données dans votre jeu d’attributs de clé. Sinon, vous pouvez avoir un pool distinct pour chaque base de données, qui ne peut être appropriée dans les applications de niveau intermédiaire, où les clients utilisent différentes chaînes de connexion différents.  
  
 Chaque fois que vous réutilisez une connexion qui a une incompatibilité d’attribut, vous devez réinitialiser les attributs qui ne correspondent pas, en fonction de la nouvelle requête de l’application, afin que la connexion retournée est identique à la demande d’application (voir la discussion de l’attribut SQL_ATTR _DBC_INFO_TOKEN dans [fonction SQLSetConnectAttr](https://go.microsoft.com/fwlink/?LinkId=59368)). Toutefois, la réinitialisation de ces attributs peut diminuer les performances. Par exemple, la réinitialisation d’une base de données nécessite un appel de réseau au serveur. Par conséquent, réutiliser une connexion qui est parfaitement mis en correspondance, si celle-ci est disponible.  
  
 Une fonction de contrôle d’accès dans le pilote peut évaluer une connexion existante avec une nouvelle demande de connexion. Par exemple, la fonction de contrôle d’accès du pilote peut déterminer :  
  
-   Si la connexion existante est parfaitement mis en correspondance avec la demande.  
  
-   S’il existe uniquement certains non significatifs incompatibilités, telles que le délai de connexion, qui ne nécessitent pas de communication avec le serveur à réinitialiser.  
  
-   S’il existe certains attributs incompatibles qui nécessitent une communication avec le serveur à réinitialiser mais entraînent encore de meilleures performances que l’établissement d’une nouvelle connexion.  
  
-   Si l’incompatibles s’est produite pour un attribut qui prend beaucoup de temps à réinitialiser (le développeur du pilote peut prendre en compte l’ajout de cet attribut dans l’ensemble des attributs de clé, qui est utilisé pour générer l’ID du pool).  
  
 Un score compris entre 0 et 100 est possible, où 0 signifie ne réutilisez pas et 100 signifie que parfaitement mis en correspondance. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) est la fonction d’évaluation d’une connexion.  
  
## <a name="new-odbc-handle---sqlhandledbcinfotoken"></a>Nouveau Handle ODBC - SQL_HANDLE_DBC_INFO_TOKEN  
 Pour prendre en charge le regroupement de connexions prenant en charge les pilotes, le pilote a besoin des informations de connexion pour calculer l’ID de Pool. Le pilote doit également les informations de connexion à comparer les nouvelles demandes de connexion avec les connexions dans le pool.  Chaque fois qu’aucune connexion dans le pool ne peut être réutilisée, le pilote doit établir une nouvelle connexion, ce qui nécessite des informations de connexion.  
  
 Dans la mesure où les informations de connexion peuvent provenir de plusieurs sources (chaîne de connexion, les attributs de connexion et DSN), le pilote peut-être analyser la chaîne de connexion et de résoudre le conflit entre ces sources dans chacun de l’appel de fonction ci-dessus.  
  
 Par conséquent, un nouveau handle ODBC est introduit : SQL_HANDLE_DBC_INFO_TOKEN. Avec SQL_HANDLE_DBC_INFO_TOKEN, un pilote est inutile analyser la chaîne de connexion et de résoudre les conflits dans les informations de connexion plusieurs fois. Dans la mesure où il s’agit d’une structure de données spécifique au pilote, le pilote peut stocker des données telles que les informations de connexion ou ID de pool.  
  
 Ce handle est uniquement utilisé comme une interface entre le Gestionnaire de pilotes et le pilote. Une application ne peut pas allouer ce handle directement.  
  
 Handle parent de ce handle est de type SQL_HANDLE_ENV, ce qui signifie que le pilote peut obtenir les informations d’environnement à partir du handle HENV lors de la résolution des informations de connexion.  
  
 Quand elle reçoit une nouvelle demande de connexion, le Gestionnaire de pilotes alloue un descripteur de type SQL_HANDLE_DBC_INFO_TOKEN pour stocker les informations de connexion, une fois que cela confirme que le pilote prend en charge la reconnaissance des pools de connexion. Une fois à l’aide de la poignée (mais avant de renvoyer certains codes différent de SQL_STILL_EXECUTING à partir de retour [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ou [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), le Gestionnaire de pilotes permettra de libérer le handle. Par conséquent, le handle est créé après l’appel de SQLAllocHandle et détruit après l’appel de SQLFreeHandle. Le Gestionnaire de pilotes garantit que le handle sera libéré avant de libérer son HENV associé (lorsque [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ou [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) retourne une erreur).  
  
 Le pilote doit modifier les fonctions suivantes pour accepter le nouveau type de handle SQL_HANDLE_DBC_INFO_TOKEN :  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Le Gestionnaire de pilotes garantit que plusieurs threads n’utilisent pas le même handle SQL_HANDLE_DBC_INFO_TOKEN simultanément. Par conséquent, le modèle de synchronisation de ce handle peut être très simple à l’intérieur du pilote. Le Gestionnaire de pilotes ne prendra pas un verrou de l’environnement avant l’allocation et libération de SQL_HANDLE_DBC_INFO_TOKEN.  
  
 Le Gestionnaire de pilotes **SQLAllocHandle** et **SQLFreeHandle** n’acceptera pas de ce nouveau type de handle.  
  
 SQL_HANDLE_DBC_INFO_TOKEN peut contenir des informations confidentielles telles que des informations d’identification. Par conséquent, un pilote doit effacer en toute sécurité de la mémoire tampon (à l’aide de [SecureZeroMemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)) qui contient les informations sensibles avant de libérer ce handle avec **SQLFreeHandle**. Chaque fois que le handle d’environnement d’une application est fermée, tous les pools de connexion associée va être fermées.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Pool de connexions du Gestionnaire de pilotes Rating algorithme  
 Cette section décrit l’algorithme de classement pour le regroupement de connexions de gestionnaire de pilotes. Les développeurs de pilotes peuvent implémenter le même algorithme pour la compatibilité descendante. Cet algorithme ne peut pas être le mieux adapté. Vous devez affiner cette algorithme en fonction de votre implémentation (dans le cas contraire, il est inutile d’implémenter cette fonctionnalité).  
  
 Le Gestionnaire de pilotes retournera une évaluation intégrale à partir de 0 à 100 pour chaque connexion à partir du pool. 0 signifie que la connexion ne peuvent pas être réutilisée et 100 indique une correspondance de la solution idéale. Supposons que la demande de connexion est nommée hRequest et la connexion existante à partir du pool est nommée en tant que hCandidate. Si l’une des conditions suivantes a la valeur false, la connexion regroupée hCandidate ne peut pas être réutilisé pour hRequest (le Gestionnaire de pilotes affectera une évaluation égale à 0).  
  
-   hCandidate et hRequest proviennent de l’API de UNICODE (par exemple, SQLDriverConnectW) ou les API ANSI (par exemple, SQLDriverConnectA). (Pilotes UNICODE peuvent le comportement différent, étant donné les API ANSI et UNICODE API (voir l’attribut de connexion SQL_ATTR_ANSI_APP).)  
  
-   hCandidate et hRequest sont créés par la même fonction ; SQLDriverConnect ou SQLConnect.  
  
-   La chaîne de connexion utilisée pour ouvrir hCandidate doit être identique à hRequest, lorsque SQLDriverConnect est utilisé.  
  
-   Le nom d’utilisateur ServerName (ou DSN), et le mot de passe utilisé pour ouvrir hCandidate doit être identique à celui utilisé pour ouvrir hRequest lorsque SQLConnect est utilisé.  
  
-   L’identificateur de sécurité (SID) du thread actuel doit être le même que le SID est utilisé pour ouvrir hCandidate.  
  
-   Pour le pilote est coûteuse inscrire et désinscrire (consultez la discussion de SQL_DTC_TRANSITION_COST dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), réutilisation *hRequest* ne doit pas nécessiter une inscription supplémentaire ou un unenlistment.  
  
 Le tableau suivant présente l’affectation de score pour différents scénarios.  
  
|Comparaison sur des attributs de connexion entre la demande et de la connexion regroupée|Aucune inscription / unenlistment|Exiger l’inscription supplémentaire / Unenlistment|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Catalogue (SQL_ATTR_CURRENT_CATALOG) est différent|60|50|  
|Certains attributs de connexion sont différents, mais le catalogue est le même|90|70|  
|Tous les attributs de connexion parfaitement mis en correspondance.|100|80|  
  
## <a name="sequence-diagram"></a>Diagramme de séquence  
 Ce diagramme de séquence montre le mécanisme de regroupement base décrit dans cette rubrique. Il affiche uniquement l’utilisation de [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) mais le [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) cas est similaire.  
  
 ![Diagramme de séquence](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Diagramme d'état  
 Ce diagramme d’état indique l’objet info jeton de connexion, décrit dans cette rubrique. Le diagramme montre uniquement [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) mais le [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) cas est similaire. Étant donné que le Gestionnaire de pilotes devrez peut-être gérer les erreurs à tout moment, le Gestionnaire de pilotes peut appeler [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) pour n’importe quel état.  
  
 ![Diagramme d’état](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>Voir aussi  
 [Le regroupement de connexions prenant en charge de pilote](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Informations de référence sur l’interface SPI ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)
