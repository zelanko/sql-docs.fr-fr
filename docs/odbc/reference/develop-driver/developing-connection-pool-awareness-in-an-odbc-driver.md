---
title: Développer la sensibilisation à la piscine de connexion dans un conducteur oDBC (fr) Microsoft Docs
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
ms.openlocfilehash: f77fea1d8439ac9ce7374b7dd47db5665686cfbc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283429"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Développement de la reconnaissance des pools de connexions dans un pilote ODBC
Ce sujet traite des détails de l’élaboration d’un conducteur ODBC qui contient des informations sur la façon dont le conducteur devrait fournir des services de mise en commun des connexions.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Permettre la mise en commun des connexions conscientes du conducteur  
 Un pilote doit implémenter les fonctions suivantes de l’interface des fournisseurs de services ODBC (SPI) :  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo (en anglais)  
  
-   SQLSetDriverConnectInfo (en anglais)  
  
-   SQLGetPoolID (SQLGetPoolID)  
  
-   SQLRateConnection (SQLRateConnection)  
  
-   SQLPoolConnect (SQLPoolConnect)  
  
-   SQLCleanupConnectionPoolID (EN anglais)  
  
 Voir [ODBC Service Provider Interface (SPI) Référence](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) pour plus d’informations.  
  
 Un conducteur doit également mettre en œuvre les fonctions existantes suivantes afin que la mise en commun consciente du conducteur puisse être activée :  
  
|Fonction|Fonctionnalité ajoutée|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Prendre en charge le nouveau type de poignée : SQL_HANDLE_DBC_INFO_TOKEN (voir la description ci-dessous).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Prendre en charge le nouvel attribut de connexion défini uniquement : SQL_ATTR_DBC_INFO_TOKEN pour la réinitialisation de la connexion (voir la description ci-dessous).|  
  
> [!NOTE]  
>  Les fonctions dépréciées telles que **SQLError** et **SQLSetConnectOption** ne sont pas prises en charge pour la mise en commun des connexions conscientes du conducteur.  
  
## <a name="the-pool-id"></a>L’ID de piscine  
 L’ID de la piscine est une pièce d’identité spécifique au conducteur pour représenter un groupe particulier de connexions qui peuvent être utilisées de manière interchangeable. Compte tenu d’un ensemble d’informations de connexion, un conducteur doit être en mesure de déduire rapidement l’ID de piscine correspondant.  
  
 Par exemple, l’ID de piscine doit encoder le nom du serveur et les informations d’identification. Cependant, le nom de base de données n’est pas nécessaire parce qu’un pilote peut être en mesure de réutiliser une connexion, puis de modifier la base de données en moins de temps que de faire une nouvelle connexion.  
  
 Un conducteur doit définir un ensemble d’attributs clés, qui comprendra l’ID de la piscine. La valeur de ces attributs clés peut provenir des attributs de connexion, de la chaîne de connexion et du DSN. Dans le cas où il y a des conflits dans ces sources, la politique de résolution existante, spécifique au conducteur, devrait être utilisée pour la compatibilité rétrograde.  
  
 Le Driver Manager utilisera une piscine différente pour différentes ID de piscine. Toutes les connexions dans la même piscine sont réutilisables. Le Driver Manager ne réutilisera jamais une connexion avec une autre pièce d’identité de piscine.  
  
 Par conséquent, les conducteurs doivent attribuer une pièce d’identité de piscine unique pour chaque groupe de connexions ayant la même valeur dans leurs attributs clés définis. Si un conducteur utilise la même pièce d’identité de piscine pour deux connexions avec des valeurs différentes dans ses attributs clés, le gestionnaire de conducteur les mettra toujours dans la même piscine (le gestionnaire de conducteur ne sait rien sur les attributs clés spécifiques au conducteur). Cela signifie que le conducteur devra signaler au gestionnaire de pilote qu’une connexion avec un ensemble différent d’attributs clés n’est pas réutilisable à l’intérieur [de la fonction SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md). Cela peut diminuer les performances et ce n’est pas recommandé.  
  
 Le gestionnaire de conducteur ne réutilisera pas une connexion allouée à partir d’un autre environnement de conducteur, même si toutes les informations de connexion correspondent. Le Driver Manager utilisera une piscine différente pour un environnement différent, même lorsque les connexions ont la même carte d’identité de piscine. Par conséquent, l’ID de la piscine est local à son environnement conducteur.  
  
 La fonction pour obtenir l’ID de piscine du conducteur est [SQLGetPoolID Fonction](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>La cote de connexion  
 Par rapport à l’établissement d’une nouvelle connexion, vous pouvez obtenir de meilleures performances en réinitialisant certaines informations de connexion (telles que DATABASE) dans une connexion mutualisée. Donc, vous ne voudrez peut-être pas que le nom de base de données soit dans votre ensemble d’attributs clés. Sinon, vous pouvez disposer d’un pool séparé pour chaque base de données, ce qui peut ne pas être bon dans les applications de niveau intermédiaire, où les clients utilisent différentes chaînes de connexion différentes.  
  
 Chaque fois que vous réutilisez une connexion qui a un certain décalage d’attribut, vous devez réinitialiser les attributs dépareillés basés sur la nouvelle demande d’application, de sorte que la connexion retournée est identique à la demande d’application (voir la discussion de l’attribut SQL_ATTR_DBC_INFO_TOKEN dans [SQLSetConnectAttr Fonction](https://go.microsoft.com/fwlink/?LinkId=59368)). Toutefois, la réinitialisation de ces attributs peut diminuer les performances. Par exemple, la réinitialisation d’une base de données nécessite un appel réseau vers le serveur. Par conséquent, réutiliser une connexion qui est parfaitement assortie, si l’on est disponible.  
  
 Une fonction d’évaluation dans le conducteur peut évaluer une connexion existante avec une nouvelle demande de connexion. Par exemple, la fonction d’évaluation du conducteur peut déterminer :  
  
-   Si la connexion existante est parfaitement assortie à la demande.  
  
-   S’il n’y a que quelques décalages insignifiants, tels que le délai de connexion, qui ne nécessitent pas de communication avec le serveur pour réinitialiser.  
  
-   S’il y a des attributs dépareillés qui nécessitent une communication avec le serveur pour réinitialiser, mais qui se traduiraient toujours par de meilleures performances que l’établissement d’une nouvelle connexion.  
  
-   Si l’incompatibilité s’est produite pour un attribut qui prend beaucoup de temps à réinitialiser (le développeur du pilote peut envisager d’ajouter cet attribut dans l’ensemble des attributs clés, qui est utilisé pour générer l’ID de la piscine).  
  
 Un score compris entre 0 et 100 est possible, où 0 moyens ne réutilisent pas et 100 signifie parfaitement assortis. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) est la fonction de notation d’une connexion.  
  
## <a name="new-odbc-handle---sql_handle_dbc_info_token"></a>Nouvelle poignée ODBC - SQL_HANDLE_DBC_INFO_TOKEN  
 Pour soutenir la mise en commun des connexions conscientes du conducteur, le conducteur a besoin d’informations de connexion pour calculer l’ID de piscine. Le conducteur a également besoin d’informations de connexion pour comparer les nouvelles demandes de connexion avec les connexions dans le pool.  Chaque fois qu’aucune connexion dans la piscine ne peut être réutilisée, le conducteur doit établir une nouvelle connexion, nécessitant ainsi des informations de connexion.  
  
 Étant donné que les informations de connexion peuvent provenir de sources multiples (chaîne de connexion, attributs de connexion et DSN), le conducteur peut avoir besoin d’analyser la chaîne de connexion et de résoudre le conflit entre ces sources dans chacun des appels de fonction ci-dessus.  
  
 Par conséquent, une nouvelle poignée ODBC est introduite : SQL_HANDLE_DBC_INFO_TOKEN. Avec SQL_HANDLE_DBC_INFO_TOKEN, un pilote n’a pas besoin d’analyser la chaîne de connexion et de résoudre les conflits dans les informations de connexion plus d’une fois. Puisqu’il s’agit d’une structure de données spécifique au conducteur, le conducteur peut stocker des données telles que des informations de connexion ou une pièce d’identité de piscine.  
  
 Cette poignée n’est utilisée qu’en interface entre le Driver Manager et le pilote. Une application ne peut pas allouer directement cette poignée.  
  
 La poignée parente de cette poignée est de type SQL_HANDLE_ENV, ce qui signifie que le conducteur peut obtenir les informations sur l’environnement de la poignée HENV lors de la résolution des informations de connexion.  
  
 Chaque fois qu’il reçoit une nouvelle demande de connexion, le gestionnaire de conducteur allouera une poignée de type SQL_HANDLE_DBC_INFO_TOKEN pour stocker les informations de connexion, après qu’il confirme que le conducteur prend en charge la connaissance de la piscine de connexion. Une fois terminé à l’aide de la poignée (mais avant de retourner quelques codes de retour autres que SQL_STILL_EXECUTING de [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ou [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), le gestionnaire de conducteur va libérer la poignée. Par conséquent, la poignée est créée après l’appel SQLAllocHandle, et détruite après l’appel SQLFreeHandle. Le Gestionnaire de conducteur garantit que la poignée sera libérée avant de libérer son HENV associé (lorsque [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ou [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) renvoie une erreur).  
  
 Le conducteur doit modifier les fonctions suivantes pour accepter le nouveau type de poignée SQL_HANDLE_DBC_INFO_TOKEN :  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Le Driver Manager garantit que plusieurs threads n’utiliseront pas le même SQL_HANDLE_DBC_INFO_TOKEN poignée simultanément. Par conséquent, le modèle de synchronisation de cette poignée peut être très simple à l’intérieur du conducteur. Le gestionnaire de conducteur ne prendra pas un verrou d’environnement avant d’allouer et de libérer SQL_HANDLE_DBC_INFO_TOKEN.  
  
 Le gestionnaire de conducteur **SQLAllocHandle** et **SQLFreeHandle** n’accepteront pas ce nouveau type de poignée.  
  
 SQL_HANDLE_DBC_INFO_TOKEN peuvent contenir des informations confidentielles telles que des informations d’identification. Par conséquent, un conducteur doit effacer en toute sécurité le tampon de mémoire (en utilisant [SecureZeroMemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)) qui contient les informations sensibles avant de libérer cette poignée avec **SQLFreeHandle**. Chaque fois que la poignée d’environnement d’une application est fermée, toutes les piscines de connexion associées seront fermées.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Algorithme d’évaluation de piscine de connexion de gestionnaire de conducteur  
 Cette section traite de l’algorithme de notation pour la mise en commun des connexions Driver Manager. Les développeurs de pilotes peuvent implémenter le même algorithme pour la compatibilité vers l’arrière. Cet algorithme n’est peut-être pas le meilleur. Vous devez affiner cet algorithme en fonction de votre implémentation (sinon, il n’y a aucune raison de implémenter cette fonctionnalité).  
  
 Le gestionnaire de conducteur retournera une note intégrale de 0 à 100 pour chaque connexion à partir de la piscine. 0 signifie que la connexion ne peut pas être réutilisée et 100 indique un ajustement parfait. Supposons que la demande de connexion est nommée hRequest et la connexion existante de la piscine est nommée hCandidate. Si l’une des conditions suivantes est fausse, la connexion mutualisée hCandidate ne peut pas être réutilisée pour hRequest (le gestionnaire de conducteur attribuera une cote de 0).  
  
-   hCandidate et hRequest proviennent tous deux de l’API UNICODE (comme SQLDriverConnectW) ou de l’API ANSI (comme SQLDriverConnectA). (Les conducteurs UNICODE peuvent avoir un comportement différent compte tenu de l’API ANSI et de l’API UNICODE (voir l’attribut de connexion SQL_ATTR_ANSI_APP).)  
  
-   hCandidate et hRequest sont créés par la même fonction; SQLDriverConnect ou SQLConnect.  
  
-   La chaîne de connexion utilisée pour ouvrir le hCandidate doit être la même que hRequest, lorsque SQLDriverConnect est utilisé.  
  
-   Le ServerName (ou DSN), le nom d’utilisateur et le mot de passe utilisé pour ouvrir hCandidate doivent être les mêmes utilisés pour ouvrir hRequest lorsque SQLConnect est utilisé.  
  
-   L’identifiant de sécurité (SID) du thread actuel doit être le même que le PEID utilisé pour ouvrir le hCandidate.  
  
-   Pour le conducteur qui coûte cher à enrôler et à ne pas s’enrôler (voir la discussion de SQL_DTC_TRANSITION_COST dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), la réutilation *hRequest* ne doit pas nécessiter un enrôlement supplémentaire ou un non-inscription.  
  
 Le tableau suivant montre l’affectation de score pour différents scénarios.  
  
|Comparaison des attributs de connexion entre la connexion mise en commun et la demande|Pas d’enrôlement / non-listation|Exiger un enrôlement supplémentaire / Unenlistment|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Catalogue (SQL_ATTR_CURRENT_CATALOG) est différent|60|50|  
|Certains attributs de connexion sont différents, mais le catalogue est le même|90|70|  
|Tous les attributs de connexion parfaitement assortis|100|80|  
  
## <a name="sequence-diagram"></a>Diagramme de séquence  
 Ce diagramme de séquence montre le mécanisme de mise en commun de base décrit dans ce sujet. Il ne montre que l’utilisation de [SQLDriverConnect,](../../../odbc/reference/syntax/sqldriverconnect-function.md) mais le boîtier [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) est similaire.  
  
 ![Diagramme de séquence](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Diagramme d'état  
 Ce diagramme d’état montre l’objet symbolique d’information de connexion, décrit dans ce sujet. Le diagramme montre seulement [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) mais le boîtier [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) est similaire. Étant donné que le gestionnaire de conducteur peut avoir besoin de gérer les erreurs à tout moment, le gestionnaire de conducteur peut appeler [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) pour n’importe quel état.  
  
 ![Diagramme d’état](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Informations de référence sur l’interface SPI ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)
