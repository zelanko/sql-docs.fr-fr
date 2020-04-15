---
title: Mise en commun de connexion de gestionnaire de conducteur (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 84ccc0db8f9a54eecc8337ca5efbc7b4c4baa239
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305820"
---
# <a name="driver-manager-connection-pooling"></a>Regroupement de connexions du gestionnaire de pilotes
La mise en commun des connexions permet à une application d’utiliser une connexion à partir d’un pool de connexions qui n’ont pas besoin d’être rétablies pour chaque utilisation. Une fois qu’une connexion a été créée et placée dans une piscine, une application peut réutiliser cette connexion sans effectuer le processus de connexion complet.  
  
 L’utilisation d’une connexion mise en commun peut entraîner des gains de performances importants, car les applications peuvent enregistrer les frais généraux impliqués dans la réalisation d’une connexion. Cela peut être particulièrement important pour les applications de niveau intermédiaire qui se connectent sur un réseau ou pour les applications qui se connectent et se déconnectent à plusieurs reprises, telles que les applications Internet.  
  
 En plus des gains de performance, l’architecture de mise en commun des connexions permet d’utiliser un environnement et ses connexions associées par plusieurs composants en un seul processus. Cela signifie que les composants autonomes dans le même processus peuvent interagir les uns avec les autres sans être conscients les uns des autres. Une connexion dans un pool de connexion peut être utilisée à plusieurs reprises par plusieurs composants.  
  
> [!NOTE]
>  La mise en commun des connexions peut être utilisée par une application ODBC présentant ODBC 2. *x* comportement, tant que l’application peut appeler *SQLSetEnvAttr*. Lors de l’utilisation de la mise en commun des connexions, l’application ne \<doit pas exécuter les instructions SQL qui modifient la base de données ou le contexte de la base de données, comme la modification du nom de *base de données*>, qui modifie le catalogue utilisé par une source de données.  


 Un pilote ODBC doit être entièrement sûr de fil, et les connexions ne doivent pas avoir d’affinité de fil pour prendre en charge la mise en commun des connexions. Cela signifie que le pilote est capable de gérer un appel sur n’importe quel thread à tout moment et est capable de se connecter sur un thread, d’utiliser la connexion sur un autre thread, et de se déconnecter sur un troisième thread.  
  
 La piscine de connexion est maintenue par le Driver Manager. Les connexions sont tirées de la piscine lorsque l’application appelle **SQLConnect** ou **SQLDriverConnect** et sont retournées à la piscine lorsque l’application appelle **SQLDisconnect**. La taille de la piscine augmente dynamiquement, en fonction des allocations de ressources demandées. Il se rétrécit en fonction du délai d’inactivité : si une connexion est inactive pendant un certain temps (elle n’a pas été utilisée dans une connexion), elle est retirée de la piscine. La taille de la piscine n’est limitée que par des contraintes de mémoire et des limites sur le serveur.  
  
 Le gestionnaire de conducteur détermine si une connexion spécifique dans un pool doit être utilisée en fonction des arguments adoptés dans **SQLConnect** ou **SQLDriverConnect**, et selon les attributs de connexion définis après l’attribution de la connexion.  
  
 Lorsque le Gestionnaire de pilote met en commun les connexions, il doit être en mesure de déterminer si une connexion fonctionne toujours avant de distribuer la connexion. Dans le cas contraire, le gestionnaire de conducteur continue de distribuer la connexion morte à l’application chaque fois qu’une défaillance transitoire du réseau se produit. Un nouvel attribut de connexion a été défini dans ODBC 3 *.x*: SQL_ATTR_CONNECTION_DEAD. Il s’agit d’un attribut de connexion de lecture uniquement qui renvoie SQL_CD_TRUE ou SQL_CD_FALSE. La valeur SQL_CD_TRUE signifie que la connexion a été perdue, tandis que la valeur SQL_CD_FALSE signifie que la connexion est toujours active. (Les conducteurs conformes aux versions antérieures d’ODBC peuvent également prendre en charge cet attribut.)  
  
 Un conducteur doit implémenter cette option efficacement ou il va nuire aux performances de mise en commun des connexions. Plus précisément, un appel pour obtenir cet attribut de connexion ne devrait pas provoquer un aller-retour sur le serveur. Au lieu de cela, un conducteur devrait simplement retourner le dernier état connu de la connexion. La connexion est morte si le dernier voyage sur le serveur a échoué, et pas mort si le dernier voyage a réussi.  
  
## <a name="remarks"></a>Notes  
 Si une connexion a été perdue (signalée par l’intermédiaire de SQL_ATTR_CONNECTION_DEAD), le gestionnaire de conduite de l’ODBC détruira cette connexion en appelant SQLDisconnect au conducteur. Les nouvelles demandes de connexion pourraient ne pas trouver de connexion utilisable dans la piscine. Finalement, le Driver Manager pourrait faire une nouvelle connexion, en supposant que la piscine est vide.  
  
 Pour utiliser un pool de connexion, une application effectue les étapes suivantes :  
  
1.  Permet la mise en commun des connexions en appelant **SQLSetEnvAttr** pour définir l’attribut SQL_ATTR_CONNECTION_POOLING environnement à SQL_CP_ONE_PER_DRIVER ou SQL_CP_ONE_PER_HENV. Cet appel doit être effectué avant que l’application n’attribue l’environnement partagé pour lequel la mise en commun des connexions doit être activée. La poignée d’environnement dans l’appel à **SQLSetEnvAttr** doit être réglée à nul, ce qui rend SQL_ATTR_CONNECTION_POOLING un attribut de niveau processus. Si l’attribut est réglé pour SQL_CP_ONE_PER_DRIVER, un pool de connexion unique est pris en charge pour chaque conducteur. Si une application fonctionne avec de nombreux pilotes et peu d’environnements, cela pourrait être plus efficace parce que moins de comparaisons peuvent être nécessaires. Si elle est réglée pour SQL_CP_ONE_PER_HENV, un pool de connexion unique est pris en charge pour chaque environnement. Si une application fonctionne avec de nombreux environnements et peu de pilotes, cela pourrait être plus efficace parce que moins de comparaisons peuvent être nécessaires. La mise en commun des connexions est désactivée en fixant SQL_ATTR_CONNECTION_POOLING à SQL_CP_OFF.  
  
2.  Alloue un environnement en appelant **SQLAllocHandle** avec l’argument *HandleType* mis à SQL_HANDLE_ENV. L’environnement alloué par cet appel sera un environnement implicite partagé car la mise en commun des connexions a été activée. L’environnement à utiliser n’est pas déterminé, cependant, jusqu’à ce que **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC est appelé sur cet environnement.  
  
3.  Alloue une connexion en appelant **SQLAllocHandle** avec *InputHandle* réglé pour SQL_HANDLE_DBC, et *l’ensemble InputHandle* à la poignée environnement allouée pour la mise en commun des connexions. Le Gestionnaire de pilote tente de trouver un environnement existant qui correspond aux attributs de l’environnement définis par l’application. S’il n’existe pas de tel environnement, on en crée un, avec un décompte de référence (maintenu par le Driver Manager) de 1. Si un environnement partagé assorti est trouvé, l’environnement est retourné à l’application et son nombre de références est incrémenté. (La connexion réelle à utiliser n’est pas déterminée par le gestionnaire de conducteur jusqu’à ce que **SQLConnect** ou **SQLDriverConnect** soit appelé.)  
  
4.  Appelle **SQLConnect** ou **SQLDriverConnect** pour effectuer la connexion. Le gestionnaire de chauffeur utilise les options de connexion dans l’appel à **SQLConnect** (ou les mots clés de connexion dans l’appel à **SQLDriverConnect**) et les attributs de connexion définis après l’attribution de connexion pour déterminer quelle connexion dans le pool doit être utilisée.  
  
    > [!NOTE]  
    >  La façon dont une connexion demandée est appariée à une connexion mise en commun est déterminée par l’attribut SQL_ATTR_CP_MATCH environnement. Pour plus d’informations, voir [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
     Les applications ODBC utilisant la mise en commun des connexions doivent appeler [CoInitializeEx](https://go.microsoft.com/fwlink/?LinkID=116307) lors de l’initialisation de [l’application et CoUninitialize](https://go.microsoft.com/fwlink/?LinkId=116310) lorsque l’application se termine.  
  
5.  Appels **SQLDisconnect** lorsqu’il est fait avec la connexion. La connexion est retournée à la piscine de connexion et devient disponible pour la réutilisation.  
  
 Pour une discussion approfondie, voir [Pooling dans les composants Microsoft Data Access](https://go.microsoft.com/fwlink/?LinkId=120776).  
  
## <a name="connection-pooling-considerations"></a>Considérations de mise en commun des connexions  
 L’exécution de l’une ou l’autre des actions suivantes à l’aide d’une commande SQL (plutôt que par l’intermédiaire de l’API ODBC) peut affecter l’état de la connexion et causer des problèmes imprévus lorsque la mise en commun des connexions est active :  
  
-   Ouverture d’une connexion et modification de la base de données par défaut.  
  
-   Utilisation de la déclaration SET pour modifier toutes les options configurables (y compris SET ROWCOUNT, ANSI_NULL, IMPLICIT_TRANSACTIONS, SHOWPLAN, STATISTICS, TEXTSIZE et DATEFORMAT).  
  
-   Création de tables temporaires et procédures stockées.  
  
 Si l’une de ces actions est effectuée en dehors de l’API ODBC, la prochaine personne qui utilise la connexion héritera automatiquement des paramètres, tableaux ou procédures précédents.  
  
> [!NOTE]  
>  Ne vous attendez pas à ce que certains paramètres soient présents dans l’état de connexion. Vous devez toujours définir l’état de connexion dans votre application et vous assurer que l’application supprime tous les paramètres de mise en commun des connexions inutilisés.  
  
## <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
 À partir de Windows 8, un pilote ODBC peut utiliser plus efficacement les connexions dans la piscine. Pour plus d’informations, voir [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à une source de données ou à un pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)   
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun dans les composants Microsoft Data Access](https://go.microsoft.com/fwlink/?LinkId=120776)
