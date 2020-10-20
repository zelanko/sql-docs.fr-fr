---
description: Développement de la reconnaissance des pools de connexions dans un pilote ODBC
title: Développement Connection-Pool de la sensibilisation dans un pilote ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f22be001a7434c13158deae8677b8c7bcb2f0630
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192309"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Développement de la reconnaissance des pools de connexions dans un pilote ODBC
Cette rubrique décrit en détail le développement d’un pilote ODBC qui contient des informations sur la façon dont le pilote doit fournir des services de regroupement de connexions.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Activation du regroupement de connexions Driver-Aware  
 Un pilote doit implémenter les fonctions SPI (Service Provider Interface) ODBC suivantes :  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 Pour plus d’informations, consultez informations de référence sur l' [interface SPI (Service Provider Interface) ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) .  
  
 Un pilote doit également implémenter les fonctions existantes suivantes afin que le regroupement reconnaissant les pilotes puisse être activé :  
  
|Fonction|Fonctionnalités ajoutées|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Prenez en charge le nouveau type de handle : SQL_HANDLE_DBC_INFO_TOKEN (voir la description ci-dessous).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Prise en charge du nouvel attribut de connexion Set-only : SQL_ATTR_DBC_INFO_TOKEN pour réinitialiser la connexion (voir la description ci-dessous).|  
  
> [!NOTE]  
>  Les fonctions déconseillées telles que **SQLError** et **SQLSetConnectOption** ne sont pas prises en charge pour le regroupement de connexions prenant en charge les pilotes.  
  
## <a name="the-pool-id"></a>L’ID du pool  
 L’ID du pool est un ID spécifique au pilote de longueur du pointeur qui représente un groupe particulier de connexions qui peuvent être utilisées indifféremment. En raison d’un ensemble d’informations de connexion, un pilote doit être en mesure de déduire rapidement l’ID de pool correspondant.  
  
 Par exemple, l’ID du pool doit encoder le nom du serveur et les informations d’identification. Toutefois, le nom de la base de données n’est pas nécessaire car un pilote peut être en mesure de réutiliser une connexion, puis de modifier la base de données en moins de temps que d’établir une nouvelle connexion.  
  
 Un pilote doit définir un ensemble d’attributs de clé, qui comprendra l’ID du pool. La valeur de ces attributs clés peut provenir des attributs de connexion, de la chaîne de connexion et du DSN. En cas de conflit dans ces sources, la stratégie de résolution propre au pilote existante doit être utilisée pour la compatibilité descendante.  
  
 Le gestionnaire de pilotes utilisera un pool différent pour les différents ID de pool. Toutes les connexions dans le même pool sont réutilisables. Le gestionnaire de pilotes ne réutilisera jamais une connexion avec un ID de pool différent.  
  
 Par conséquent, les pilotes doivent affecter un ID de pool unique pour chaque groupe de connexions ayant la même valeur dans leurs attributs de clé définis. Si un pilote utilise le même ID de pool pour deux connexions avec des valeurs différentes dans leurs attributs de clé, le gestionnaire de pilotes les placera toujours dans le même pool (le gestionnaire de pilotes ne sait rien des attributs de clé spécifiques au pilote). Cela signifie que le pilote doit signaler au gestionnaire de pilotes qu’une connexion avec un ensemble différent d’attributs de clé n’est pas réutilisable dans la [fonction SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md). Cela peut réduire les performances, ce qui n’est pas recommandé.  
  
 Le gestionnaire de pilotes ne réutilise pas une connexion allouée à partir d’un autre environnement de pilote, même si toutes les informations de connexion correspondent. Le gestionnaire de pilotes utilise un autre pool pour différents environnements, même lorsque les connexions ont le même ID de pool. Par conséquent, l’ID de pool est local à son environnement de pilote.  
  
 La fonction permettant d’obtenir l’ID du pool à partir du pilote est [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>L’évaluation de la connexion  
 Par rapport à l’établissement d’une nouvelle connexion, vous pouvez obtenir de meilleures performances en réinitialisant certaines informations de connexion (telles que la base de données) dans une connexion regroupée. Par conséquent, il est possible que vous ne souhaitiez pas que le nom de la base de données se trouve dans votre ensemble d’attributs de clé. Dans le cas contraire, vous pouvez avoir un pool distinct pour chaque base de données, ce qui peut ne pas être correct dans les applications de niveau intermédiaire, où les clients utilisent différentes chaînes de connexion.  
  
 Chaque fois que vous réutilisez une connexion qui a des incompatibilités d’attributs, vous devez réinitialiser les attributs incompatibles en fonction de la nouvelle demande de l’application, afin que la connexion retournée soit identique à celle de la demande d’application (voir la discussion de l’attribut SQL_ATTR_DBC_INFO_TOKEN dans la [fonction SQLSetConnectAttr](../syntax/sqlsetconnectattr-function.md)). Toutefois, la réinitialisation de ces attributs peut réduire les performances. Par exemple, la réinitialisation d’une base de données nécessite un appel réseau vers le serveur. Par conséquent, réutilisez une connexion qui est parfaitement mise en correspondance, si celle-ci est disponible.  
  
 Une fonction d’évaluation dans le pilote peut évaluer une connexion existante avec une nouvelle demande de connexion. Par exemple, la fonction Rating du pilote peut déterminer les éléments suivants :  
  
-   Si la connexion existante est parfaitement mise en correspondance avec la requête.  
  
-   S’il n’existe que des incompatibilités non significatives, telles que le délai de connexion, qui ne nécessitent pas de communication avec le serveur pour être réinitialisé.  
  
-   S’il existe des attributs incompatibles qui requièrent une communication avec le serveur pour être réinitialisés, mais qui continueraient à améliorer les performances par rapport à l’établissement d’une nouvelle connexion.  
  
-   Si le problème s’est produit pour un attribut qui est très long à réinitialiser (le développeur du pilote peut envisager d’ajouter cet attribut dans le jeu d’attributs de clé, qui est utilisé pour générer l’ID de pool).  
  
 Un score compris entre 0 et 100 est possible, où 0 signifie qu’il n’y a pas de réutilisation et que 100 signifie une correspondance parfaite. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) est la fonction permettant d’évaluer une connexion.  
  
## <a name="new-odbc-handle---sql_handle_dbc_info_token"></a>Nouveau handle ODBC-SQL_HANDLE_DBC_INFO_TOKEN  
 Pour prendre en charge le regroupement de connexions prenant en charge les pilotes, le pilote a besoin des informations de connexion pour calculer l’ID du pool. Le pilote a également besoin des informations de connexion pour comparer les nouvelles demandes de connexion aux connexions dans le pool.  Chaque fois qu’aucune connexion dans le pool ne peut être réutilisée, le pilote doit établir une nouvelle connexion, ce qui nécessite des informations de connexion.  
  
 Étant donné que les informations de connexion peuvent provenir de plusieurs sources (chaîne de connexion, attributs de connexion et DSN), le pilote peut être amené à analyser la chaîne de connexion et à résoudre le conflit entre ces sources dans chacun des appels de fonction ci-dessus.  
  
 Par conséquent, un nouveau descripteur ODBC est introduit : SQL_HANDLE_DBC_INFO_TOKEN. Avec SQL_HANDLE_DBC_INFO_TOKEN, un pilote n’a pas besoin d’analyser la chaîne de connexion et de résoudre plusieurs fois les conflits dans les informations de connexion. Étant donné qu’il s’agit d’une structure de données spécifique au pilote, le pilote peut stocker des données telles que des informations de connexion ou un ID de pool.  
  
 Ce descripteur est utilisé uniquement en tant qu’interface entre le gestionnaire de pilotes et le pilote. Une application ne peut pas allouer directement ce descripteur.  
  
 Le handle parent de ce descripteur est de type SQL_HANDLE_ENV, ce qui signifie que le pilote peut obtenir les informations d’environnement à partir du handle HENV pendant la résolution des informations de connexion.  
  
 À chaque fois qu’il reçoit une nouvelle demande de connexion, le gestionnaire de pilotes alloue un descripteur de type SQL_HANDLE_DBC_INFO_TOKEN pour le stockage des informations de connexion, après avoir confirmé que le pilote prend en charge la reconnaissance des pools de connexions. Lorsque vous avez terminé d’utiliser le descripteur (mais avant de retourner des codes de retour autres que SQL_STILL_EXECUTING de [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ou [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), le gestionnaire de pilotes libère le descripteur. Par conséquent, le handle est créé après l’appel SQLAllocHandle et détruit après l’appel de SQLFreeHandle. Le gestionnaire de pilotes garantit que le descripteur sera libéré avant de libérer son HENV associé (quand [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ou [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) retourne une erreur).  
  
 Le pilote doit modifier les fonctions suivantes pour accepter le nouveau type de handle SQL_HANDLE_DBC_INFO_TOKEN :  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Le gestionnaire de pilotes garantit que plusieurs threads n’utiliseront pas simultanément le même SQL_HANDLE_DBC_INFO_TOKEN descripteur. Par conséquent, le modèle de synchronisation de ce descripteur peut être très simple dans le pilote. Le gestionnaire de pilotes ne prend pas de verrou d’environnement avant d’allouer et de libérer des SQL_HANDLE_DBC_INFO_TOKEN.  
  
 Le gestionnaire de pilotes **SQLAllocHandle** et **SQLFreeHandle** n’accepte pas ce nouveau type de handle.  
  
 SQL_HANDLE_DBC_INFO_TOKEN peut contenir des informations confidentielles telles que des informations d’identification. Par conséquent, un pilote doit effacer en toute sécurité la mémoire tampon (à l’aide de [SecureZeroMemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)) qui contient les informations sensibles avant de libérer ce handle avec **SQLFreeHandle**. Chaque fois qu’un descripteur d’environnement de l’application est fermé, tous les pools de connexions associés sont fermés.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Algorithme de classification du pool de connexions du gestionnaire de pilotes  
 Cette section traite de l’algorithme d’évaluation pour le regroupement de connexions du gestionnaire de pilotes. Les développeurs de pilotes peuvent implémenter le même algorithme à des fins de compatibilité descendante. Cet algorithme n’est peut-être pas le meilleur. Vous devez affiner cet algorithme en fonction de votre implémentation (sinon, il n’y a aucune raison d’implémenter cette fonctionnalité).  
  
 Le gestionnaire de pilotes renvoie une évaluation intégrale comprise entre 0 et 100 pour chaque connexion à partir du pool. 0 signifie que la connexion ne peut pas être réutilisée et 100 indique une correspondance parfaite. Supposons que la demande de connexion est nommée hRequest et que la connexion existante à partir du pool est nommée hCandidate. Si l’une des conditions suivantes est false, la hCandidate de connexion regroupée ne peut pas être réutilisée pour hRequest (le gestionnaire de pilotes attribuera une évaluation de 0).  
  
-   hCandidate et hRequest proviennent de l’API UNICODE (telle que SQLDriverConnectW) ou de l’API ANSI (comme SQLDriverConnectA). (Les pilotes UNICODE peuvent avoir un comportement différent de l’API ANSI donnée et de l’API UNICODE (Voir l’attribut de connexion SQL_ATTR_ANSI_APP).)  
  
-   hCandidate et hRequest sont créés par la même fonction. SQLDriverConnect ou SQLConnect.  
  
-   La chaîne de connexion utilisée pour ouvrir hCandidate doit être identique à hRequest, lorsque SQLDriverConnect est utilisé.  
  
-   Le nom de serveur (ou DSN), le nom d’utilisateur et le mot de passe utilisés pour ouvrir hCandidate doivent être les mêmes que ceux utilisés pour ouvrir hRequest lorsque SQLConnect est utilisé.  
  
-   L’identificateur de sécurité (SID) du thread actuel doit être le même que le SID utilisé pour ouvrir hCandidate.  
  
-   Pour le pilote qui est coûteux à inscrire et à désinscrire (voir la discussion de SQL_DTC_TRANSITION_COST dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), la réutilisation de *hRequest* ne doit pas nécessiter d’inscription ou d’annulation d’inscription supplémentaire.  
  
 Le tableau suivant montre l’attribution du score pour différents scénarios.  
  
|Comparaison des attributs de connexion entre la connexion regroupée et la demande|Aucune inscription/désinscription|Exiger une inscription/désinscription supplémentaire|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Le catalogue (SQL_ATTR_CURRENT_CATALOG) est différent|60|50|  
|Certains attributs de connexion sont différents, mais le catalogue est le même|90|70|  
|Tous les attributs de connexion sont parfaitement mis en correspondance|100|80|  
  
## <a name="sequence-diagram"></a>Diagramme de séquence  
 Ce diagramme de séquence montre le mécanisme de regroupement de base décrit dans cette rubrique. Il illustre uniquement l’utilisation de [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) , mais le cas [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) est similaire.  
  
 ![Diagramme de séquence](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Diagramme d'état  
 Ce diagramme d’état affiche l’objet de jeton d’informations de connexion, décrit dans cette rubrique. Le diagramme affiche uniquement [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) , mais le cas [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) est similaire. Étant donné que le gestionnaire de pilotes peut avoir besoin de gérer des erreurs à tout moment, le gestionnaire de pilotes peut appeler [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) pour n’importe quel état.  
  
 ![Diagramme d’état](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>Voir aussi  
 [Regroupement de connexions prenant en charge les pilotes](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Informations de référence sur l’interface SPI ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)