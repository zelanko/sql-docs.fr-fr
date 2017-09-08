---
title: "Considérations sur la sécurité pour l’apprentissage dans SQL Server | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d9b5fba856cc40c11f218faf0a61f66ee5451aa4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="security-considerations-for-machine-learning-in-sql-server"></a>Considérations sur la sécurité pour l’apprentissage dans SQL Server

Cet article répertorie les considérations de sécurité que l’administrateur ou un architecte doit-elle garder à l’esprit lors de l’utilisation des services de machine learning.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

## <a name="use-a-firewall-to-restrict-network-access-by-r"></a>Utilisez un pare-feu pour restreindre l’accès réseau par R

Dans une installation par défaut, une règle de pare-feu Windows est utilisée pour bloquer tout accès réseau sortant à partir du processus du runtime R. Des règles de pare-feu doivent être créées pour éviter que le processus d’exécution R ne télécharge des packages ou n’effectue d’autres appels réseau potentiellement malveillants.

Si vous utilisez un autre programme de pare-feu, vous pouvez également créer des règles pour bloquer les connexions réseau sortantes pour le composant d’exécution R en définissant des règles pour les comptes d’utilisateurs locaux ou pour le groupe représenté par le pool de comptes d’utilisateur.

Nous recommandons fortement d’activer le pare-feu Windows (ou un autre pare-feu de votre choix) pour empêcher l’accès au réseau sans limites par les exécutions de R ou Python.

## <a name="authentication-methods-supported-for-remote-compute-contexts"></a>Méthodes d’authentification pris en charge pour les contextes de calcul à distance

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]prend en charge les connexions à la fois l’authentification intégrée Windows et SQL lors de la création des connexions entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un client de science des données distantes.

Par exemple, si vous développez une solution R sur votre ordinateur portable et que vous voulez effectuer des calculs sur l’ordinateur SQL Server, vous devez créer une source de données SQL Server dans le code R, en utilisant les fonctions **rx** et en définissant une chaîne de connexion basée sur vos informations d’identification Windows.

Lorsque vous modifiez le _contexte de calcul_ à partir de votre ordinateur portable à l’ordinateur SQL Server, si votre compte Windows dispose des autorisations nécessaires, tout le code R est exécuté sur l’ordinateur SQL Server. En outre, toutes les requêtes SQL exécutées en tant que partie du code R sont exécutées sous également vos informations d’identification.

L’utilisation de connexions SQL est également pris en charge dans ce scénario, qui nécessite que l’instance SQL Server soit configuré pour autoriser l’authentification en mode mixte.

### <a name="implied-authentication"></a>Authentification implicite

 En règle générale, le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] démarre l’exécution du script externe et exécute des scripts sous son propre compte. Toutefois, si le runtime externe effectue un appel ODBC, le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] emprunte l’identité de l’identification de l’utilisateur qui a envoyé la commande pour vous assurer que l’appel ODBC n’échoue pas. C’est ce que l’on appelle l’*authentification implicite*.
 
 > [!IMPORTANT]
 >
 > Pour que l’authentification implicite aboutisse, le groupe d’utilisateurs Windows qui contient les comptes de travail (par défaut, **SQLRUser**) doit posséder un compte dans la base de données MASTER pour l’instance, et ce compte doit avoir reçu les autorisations permettant de se connecter à l’instance.
 > 
 > Le groupe **SQLRUser** est également utilisé lors de l’exécution de scripts Python. 

## <a name="no-support-for-encryption-at-rest"></a>Aucune prise en charge pour le chiffrement au repos

Chiffrement transparent des données n’est pas prise en charge pour les données envoyées ou reçues à partir de l’exécution du script externe. Par conséquent, le chiffrement au repos **n’est pas** être appliqué à toutes les données que vous utilisez dans les scripts R ou Python, toutes les données enregistrées sur disque, ou aucun résultat intermédiaire persistant.

## <a name="resources"></a>Ressources

Pour plus d’informations sur la gestion du service et comment configurer les comptes d’utilisateur utilisés pour exécuter des scripts R, consultez [configurer et gérer les Extensions d’Analytique avancée](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md).

Pour obtenir une description de l’architecture de sécurité, consultez :

+ [Vue d’ensemble de la sécurité pour R](security-overview-sql-server-r.md)
+ [Vue d’ensemble de la sécurité pour Python](../python/security-overview-sql-server-python-services.md)
