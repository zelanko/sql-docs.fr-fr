---
title: "Développer avec les API REST pour Reporting Services | Documents Microsoft"
ms.description: The REST API provides programmatic access to the objects in a SQL Server 2017 Reporting Services report server catalog.
ms.date: 10/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 7c2c34047ac316045387b036cf10ee149175580a
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="develop-with-the-rest-apis-for-reporting-services"></a>Développer avec les API REST pour Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)])

Microsoft SQL Server 2017 Reporting Services prend en charge le transfert de REST (Representational State) API. Les API REST service créer des points de terminaison qui prennent en charge un ensemble d’opérations HTTP (méthodes), qui fournissent, récupérer, mettre à jour ou supprimer l’accès pour les ressources au sein d’un serveur de rapports.

L’API REST fournit l’accès par programme aux objets dans un catalogue de serveur de rapports SQL Server 2017 Reporting Services. Exemples d’objets sont des dossiers, rapports, indicateurs de performance clés, les sources de données, datasets, plans d’actualisation, abonnements et bien plus encore. À l’aide de l’API REST, vous pouvez, par exemple, parcourez l’arborescence des dossiers, découvrir le contenu d’un dossier ou télécharger une définition de rapport. Vous pouvez également créer, mettre à jour et supprimer des objets. Exemples d’utilisation des objets sont télécharger un rapport, exécuter un plan d’actualisation, supprimer un dossier et ainsi de suite.

## <a name="components-of-a-rest-api-requestresponse"></a>Composants d’une API REST demande/réponse

Une paire de demande/réponse API REST peut être divisée en cinq composants :

* Le **URI de demande**, qui se compose de : `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Bien que l’URI de demande est incluse dans l’en-tête de message de demande, nous l’appelons séparément ici, car la plupart des langages ou des infrastructures nécessitent vous permettent de passer de séparément à partir du message de demande.

    * Schéma d’URI : indique le protocole utilisé pour transmettre la demande. Par exemple, `http` ou `https`.
    * Hôte de l’URI : Spécifie le nom de domaine ou l’adresse IP du serveur où le point de terminaison de service REST est hébergé, tel que `myserver.contoso.com`.
    * Chemin d’accès de ressource : Spécifie la ressource ou la collection de ressources, ce qui peut inclure plusieurs segments utilisés par le service dans la détermination de la sélection de ces ressources. Par exemple : `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` peut être utilisé pour obtenir les propriétés spécifiées pour le CatalogItem.
    * (Facultative) de la chaîne de requête : fournit des paramètres simples supplémentaires, telles que les critères de sélection de version ou une ressource API.

* Champs d’en-tête HTTP demande message :

    * Une valeur obligatoire [méthode HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (également appelé une opération ou action), qui indique au service, le type d’opération que vous avez demandée. Reporting que services REST API prennent en charge la suppression, GET, HEAD, PUT, POST et les méthodes de correctif logiciel.
    * Champs d’en-tête supplémentaire facultatif, comme requis par la méthode spécifiée de l’URI et HTTP.

* HTTP facultatif **corps de message de la demande** champs, pour prendre en charge l’opération de l’URI et HTTP. Par exemple, les opérations POST contient codé au format MIME des objets qui sont passés comme paramètres complexes. Pour les opérations POST ou PUT, le type de codage MIME pour le corps doit être spécifié dans le `Content-type` en-tête de la demande. Certains services vous obligent à utiliser un type MIME spécifique, tel que `application/json`.

* HTTP **en-tête de message de réponse** champs :

    * Un [code d’état HTTP](http://www.w3.org/Protocols/HTTP/HTRESP.html), le classement à partir des codes de réussite 2xx aux codes d’erreur 4xx ou 5xx. Vous pouvez également, un code d’état de service défini peut être retourné, comme indiqué dans la documentation de l’API.
    * Champs d’en-tête supplémentaire facultatif, comme requis pour prendre en charge de réponse de la demande, tels qu’un `Content-type` en-tête de réponse.

* HTTP facultatif **corps du message de réponse** champs :

    * Objets de codage MIME de réponse sont renvoyés dans le corps de réponse HTTP, par exemple une réponse à partir d’une méthode GET qui retourne des données. En règle générale, ces objets sont retournés dans un format structuré comme JSON ou XML, comme indiqué par la `Content-type` en-tête de réponse.

## <a name="api-documentation"></a>Documentation de l’API

Une API REST moderne appelle pour obtenir une documentation API moderne. L’API REST repose sur la spécification OpenAPI (aussi appelé) la spécification de swagger) et de la documentation est disponible sur [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0). Au-delà de la documentation de l’API, SwaggerHub permet de générer une bibliothèque cliente dans la langue choisie – JavaScript, TypeScript, c#, Java, Python, Ruby et bien plus encore.

## <a name="testing-api-calls"></a>Appels d’API de test

Un outil de test des messages de demande/réponse HTTP est [Fiddler](http://www.telerik.com/fiddler). Fiddler est un site web gratuit proxy capable d’intercepter vos demandes REST, ce qui facilite le diagnostic de la requête HTTP de débogage / messages de réponse.

## <a name="next-steps"></a>Étapes suivantes

Passez en revue les API disponibles sur de [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0).

Exemples sont disponibles sur [GitHub](https://github.com/Microsoft/Reporting-Services). L’exemple inclut une application HTML5 repose sur TypeScript et réagissent webpack avec un exemple de PowerShell.

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
