---
title: Regroupement de connexions de gestionnaire de pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling [ODBC]
- pooled connections [ODBC]
- connecting to driver [ODBC], connection pooling
- connecting to data source [ODBC], connection pooling
ms.assetid: ee95ffdb-5aa1-49a3-beb2-7695b27c3df9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e03932fe9d6cc98648c2e0da2e2cdd963a8d67f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826136"
---
# <a name="driver-manager-connection-pooling"></a>Regroupement de connexions du gestionnaire de pilotes
Le regroupement de connexions permet à une application d’utiliser une connexion à partir d’un pool de connexions qui ne doivent pas être rétablie pour chaque utilisation. Une fois qu’une connexion a été créée et placée dans un pool, une application peut réutiliser cette connexion sans effectuer le processus de connexion complète.  
  
 À l’aide d’une connexion regroupée peut entraîner des gains de performances significatifs, étant donné que les applications peuvent enregistrer la surcharge impliquée dans l’établissement d’une connexion. Cela peut être particulièrement importante pour les applications de couche intermédiaire qui se connectent via un réseau ou pour les applications qui se connectent à plusieurs reprises et de vous déconnecter, telles que les applications Internet.  
  
 En plus des gains de performances, l’architecture de regroupement de connexions permet à un environnement et les connexions associées à être utilisé par plusieurs composants dans un processus unique. Cela signifie que les composants autonomes dans le même processus peuvent interagir avec eux sans connaître les unes des autres. Une connexion dans un pool de connexions peut être utilisée à plusieurs reprises par plusieurs composants.  
  
> [!NOTE]  
>  Le regroupement de connexions peut être utilisé par une application ODBC présentant ODBC 2. *x* comportement, à condition que l’application peut appeler *SQLSetEnvAttr*. Lorsque vous utilisez le regroupement de connexions, l’application ne doit pas exécuter les instructions SQL qui modifient la base de données ou le contexte de la base de données, telles que la modification la \< *base de données ** nom*>, ce qui modifie le catalogue utilisé par un source de données.  
  
 Un pilote ODBC doit être complètement thread-safe, et les connexions ne doivent pas d’affinité de thread pour prendre en charge le regroupement de connexions. Cela signifie que le pilote est en mesure de gérer un appel sur n’importe quel thread à tout moment et est en mesure de se connecter sur un thread, à utiliser la connexion sur un autre thread et à la déconnexion sur un troisième thread.  
  
 Le pool de connexions est conservé par le Gestionnaire de pilotes. Les connexions sont retirées du pool lorsque l’application appelle **SQLConnect** ou **SQLDriverConnect** et sont retournées au pool lorsque l’application appelle **SQLDisconnect**. La taille du pool augmente dynamiquement, basé sur les allocations de la ressource demandée. Il est réduit selon le délai d’inactivité : si une connexion est inactive pendant une période de temps (il n'a pas été utilisé dans une connexion), il est supprimé à partir du pool. La taille du pool est limitée uniquement par les contraintes de mémoire et les limites sur le serveur.  
  
 Le Gestionnaire de pilotes détermine si une connexion spécifique dans un pool doit être utilisée conformément aux arguments passés dans **SQLConnect** ou **SQLDriverConnect**et selon les attributs de connexion définir une fois que la connexion a été allouée.  
  
 Lorsque le Gestionnaire de pilotes est le regroupement de connexions, il doit être en mesure de déterminer si une connexion fonctionne toujours avant la transmission de la connexion. Sinon, le Gestionnaire de pilotes conserve en distribuant la connexion à l’application chaque fois qu’une défaillance réseau temporaire se produit. Un nouvel attribut de connexion a été défini dans ODBC 3 *.x*: SQL_ATTR_CONNECTION_DEAD. Il s’agit d’un attribut de connexion en lecture seule qui retourne SQL_CD_TRUE ou SQL_CD_FALSE. La valeur SQL_CD_TRUE signifie que la connexion a été perdue, tandis que la valeur SQL_CD_FALSE signifie que la connexion est toujours active. (Pilotes conformes aux versions antérieures de ODBC peuvent également en charge cet attribut.)  
  
 Un pilote doit implémenter cette option efficacement ou nuira aux performances de regroupement de connexion. Plus précisément, un appel pour obtenir cet attribut de connexion ne doit pas provoquer un aller-retour vers le serveur. Au lieu de cela, un pilote doit simplement retourner le dernier état connu de la connexion. La connexion est inactive si le dernier voyage vers le serveur a échoué et pas morts si le dernier voyage a réussi.  
  
## <a name="remarks"></a>Notes  
 Si une connexion a été perdue (signalés par le biais de SQL_ATTR_CONNECTION_DEAD), le Gestionnaire de pilotes ODBC détruira cette connexion en appelant SQLDisconnect dans le pilote. Nouvelles demandes de connexion peut ne pas trouver une connexion utilisable dans le pool. Par la suite le Gestionnaire de pilotes peut être une nouvelle connexion, en supposant que le pool est vide.  
  
 Pour utiliser un pool de connexions, une application effectue les étapes suivantes :  
  
1.  Permet le regroupement de connexions en appelant **SQLSetEnvAttr** à la valeur de l’attribut d’environnement SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER ou SQL_CP_ONE_PER_HENV. Cet appel doit être effectué avant l’application alloue l’environnement partagé, pour quelle connexion de regroupement doit être activée. Le handle d’environnement dans l’appel à **SQLSetEnvAttr** doit être définie sur null, ce qui rend SQL_ATTR_CONNECTION_POOLING un attribut au niveau du processus. Si l’attribut est défini à SQL_CP_ONE_PER_DRIVER, un pool de connexions unique est prise en charge pour chaque pilote. Si une application fonctionne avec de nombreux pilotes et peu d’environnements, peut-être plus efficace des comparaisons moins peuvent être nécessaire. Si la valeur SQL_CP_ONE_PER_HENV, un pool de connexions unique est prise en charge pour chaque environnement. Si une application fonctionne avec peu de pilotes et de nombreux environnements, peut-être plus efficace des comparaisons moins peuvent être nécessaire. Le regroupement de connexions est désactivé en définissant SQL_ATTR_CONNECTION_POOLING sur SQL_CP_OFF.  
  
2.  Alloue un environnement en appelant **SQLAllocHandle** avec la *HandleType* argument défini à SQL_HANDLE_ENV. L’environnement alloué par cet appel peut être un environnement partagé implicit, car le regroupement de connexions a été activé. L’environnement utilisable n’est pas déterminé, toutefois, jusqu'à ce que **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC est appelée sur cet environnement.  
  
3.  Alloue une connexion en appelant **SQLAllocHandle** avec *InputHandle* ayant pour valeur SQL_HANDLE_DBC et le *InputHandle* le handle d’environnement alloué pour la valeur le regroupement de connexions. Le Gestionnaire de pilotes tente de trouver un environnement existant qui correspond aux attributs d’environnement définies par l’application. Si aucun environnement n’existe, est créé, avec un décompte de références (géré par le Gestionnaire de pilotes) de 1. Si un environnement partagé correspondant est trouvé, l’environnement est retourné à l’application et son décompte de références est incrémenté. (La connexion réelle à utiliser n’est pas déterminée par le Gestionnaire de pilote jusqu'à ce que **SQLConnect** ou **SQLDriverConnect** est appelée.)  
  
4.  Appels **SQLConnect** ou **SQLDriverConnect** pour établir la connexion. Le Gestionnaire de pilotes utilise les options de connexion dans l’appel à **SQLConnect** (ou les mots clés de connexion dans l’appel à **SQLDriverConnect**) et les attributs de connexion définie après l’allocation de connexion déterminer quelle connexion dans le pool doit être utilisée.  
  
    > [!NOTE]  
    >  Comment une connexion demandée est mis en correspondance avec une connexion regroupée est déterminée par l’attribut d’environnement SQL_ATTR_CP_MATCH. Pour plus d’informations, consultez [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
     Les applications ODBC à l’aide du regroupement de connexions doivent appeler [CoInitializeEx](http://go.microsoft.com/fwlink/?LinkID=116307) pendant l’initialisation d’application et [CoUninitialize](http://go.microsoft.com/fwlink/?LinkId=116310) lorsque l’application se ferme.  
  
5.  Appels **SQLDisconnect** lorsque vous avez terminé avec la connexion. La connexion est retournée au pool de connexions et devient disponible pour une réutilisation.  
  
 Pour une présentation détaillée, consultez [le regroupement dans le Microsoft Data Access Components](http://go.microsoft.com/fwlink/?LinkId=120776).  
  
## <a name="connection-pooling-considerations"></a>Considérations de regroupement de connexions  
 Exécutant une des actions suivantes à l’aide d’une commande SQL (plutôt que via l’API ODBC), vous pouvez affecter l’état de la connexion et causer des problèmes inattendus lorsque le regroupement de connexions est actif :  
  
-   Ouverture d’une connexion et la modification de la base de données par défaut.  
  
-   À l’aide de l’instruction SET pour modifier les options configurables (y compris SET ROWCOUNT ANSI_NULL, IMPLICIT_TRANSACTIONS, SHOWPLAN, statistiques, TEXTSIZE et DATEFORMAT).  
  
-   Création de tables temporaires et les procédures stockées.  
  
 Si une de ces actions sont effectuée en dehors de l’API ODBC, la personne suivante qui utilise la connexion héritent automatiquement des paramètres précédents, des tables ou des procédures.  
  
> [!NOTE]  
>  N’attendent pas certains paramètres dans l’état de connexion. Vous devez toujours définir l’état de connexion dans votre application et vous assurer que l’application supprime toute connexion inutilisée le regroupement de paramètres.  
  
## <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
 À compter de Windows 8, un pilote ODBC permettre utiliser les connexions dans le pool plus efficacement. Pour plus d’informations, consultez [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à une données Source ou pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)   
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement dans les Microsoft Data Access Components](http://go.microsoft.com/fwlink/?LinkId=120776)
