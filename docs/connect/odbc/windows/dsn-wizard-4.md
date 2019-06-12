---
title: Écran 4 (pilote ODBC pour SQL Server) de l’Assistant Source de données | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 93145892c96d2b255dca758e7028d2884cec359b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797767"
---
# <a name="data-source-wizard-screen-4"></a>Assistant Source de données, écran 4

Spécifiez la langue à utiliser pour les messages SQL Server et la traduction de jeu de caractères ; indiquez si ODBC Driver for SQL Server doit utiliser des paramètres régionaux. Vous pouvez également contrôler l'enregistrement des paramètres des requêtes longues et des statistiques du pilote.

## <a name="options"></a>Options

### <a name="change-the-language-of-sql-server-system-messages-to"></a>Modifier la langue des messages systèmes de SQL Server

Chaque instance de SQL Server peut avoir plusieurs jeux de messages système, chacun dans une langue différente (par exemple, anglais, espagnol, français, etc.). Si une source de données est définie contre un serveur qui possède plusieurs jeux de messages systèmes, vous pouvez spécifier la langue que vous voulez utiliser pour vos messages systèmes. Dans la liste, cliquez sur la langue. Cette option n’est pas disponible s’il n’y a qu’une seule langue installée sur SQL Server.

### <a name="use-strong-encryption-for-data"></a>Utiliser le chiffrement renforcé pour les données

Si l'option est sélectionnée, les données transférées via les connexions établies à l'aide de ce DSN seront chiffrées. Les noms de connexion sont chiffrés par défaut, même si la case à cocher est désactivée.

### <a name="trust-server-certificate"></a>Faire confiance au certificat de serveur

Cette option est applicable uniquement lorsque **utiliser un chiffrement renforcé pour les données** est activé. Quand sélectionné, il est possible que le certificat du serveur n’est pas validé pour avoir le nom d’hôte correct du serveur et être émis par une autorité de certification approuvée. 

### <a name="perform-translation-for-character-data"></a>Traduire les données de type caractère

Lorsque cette case est cochée, ODBC Driver for SQL Server convertit les chaînes ANSI envoyées entre l’ordinateur client et SQL Server avec Unicode. Le pilote ODBC fait parfois la conversion entre la page de codes SQL Server et Unicode sur l’ordinateur client. Il faut pour cela que la page de codes utilisée par SQL Server soit l’une des pages de codes disponibles sur l’ordinateur client.

Lorsque cette case à cocher est désactivée, aucune traduction de caractères étendus des chaînes de caractères ANSI n'est réalisée lorsqu'ils sont transférés entre l'application cliente et le serveur. Si l’ordinateur client utilise une page de codes ANSI (ACP) différente de celle de SQL Server, les caractères étendus présents dans les chaînes de caractères ANSI risquent d’être mal interprétés. Si l’ordinateur client utilise la même page de codes pour son ACP que SQL Server, les caractères étendus sont interprétés correctement.

### <a name="use-regional-settings-when-outputting-currency-numbers-dates-and-times"></a>Utiliser les paramètres régionaux lors de la copie de devises, de nombres, de dates et d'heures

Spécifie que le pilote utilise les paramètres régionaux de l'ordinateur client pour mettre en forme les devises, les nombres, les dates et les heures dans les chaînes de sortie de caractères. Le pilote utilise le paramètre régional par défaut pour le compte de connexion Windows de l'utilisateur qui se connecte via la source de données. Sélectionnez cette option pour les applications qui affichent uniquement les données, pas pour les applications qui traitent les données.

### <a name="save-long-running-queries-to-the-log-file"></a>Enregistrer les requêtes à long terme dans le fichier journal

Spécifie que le pilote enregistre toutes les requêtes qui dépassent la valeur **Temps des requêtes longues**. Les requêtes longues sont enregistrées dans le fichier spécifié. Pour spécifier un fichier journal, tapez le chemin d’accès complet et le nom de fichier dans la zone ou cliquez sur **Parcourir** pour sélectionner un fichier journal en naviguant parmi les répertoires de fichiers existants.

### <a name="long-query-time-milliseconds"></a>Durée de requête longue (millisecondes)

Spécifie une valeur de seuil, en millisecondes, pour l'enregistrement de requête longue. Toute requête qui prend plus de temps que cette durée en millisecondes pour s'exécuter est enregistrée.

### <a name="log-odbc-driver-statistics-to-the-log-file"></a>Enregistrer les statistiques de pilote ODBC dans le fichier journal

Spécifie que les statistiques sont enregistrées. Les statistiques sont enregistrées dans le fichier spécifié. Pour spécifier un fichier journal, tapez le chemin d’accès complet et le nom de fichier dans la zone ou cliquez sur **Parcourir** pour sélectionner un fichier journal en naviguant parmi les répertoires de fichiers existants.

Le journal de statistiques est un fichier délimité par des tabulations qui peut être analysé dans Microsoft Excel ou toute autre application qui prend en charge les fichiers délimités par des tabulations.

### <a name="connect-retry-count"></a>Nombre de nouvelles tentatives de connexion

Spécifie le nombre de tentatives d’une tentative de connexion échoue.

### <a name="connect-retry-interval-seconds"></a>Intervalle avant nouvelle tentative de connexion (en secondes)

Spécifie le nombre de secondes entre chaque nouvelle tentative de connexion. Pour plus d’informations sur le fonctionnement de ce et **nombre de tentatives de connexion** options, consultez [résilience des connexions dans le pilote ODBC de Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).

### <a name="back"></a>Précédent

Cliquez sur ce bouton pour revenir à la page précédente de l’Assistant.

### <a name="finish"></a>Terminer

Si les informations spécifiées dans cet écran sont terminées, vous pouvez cliquer sur **Terminer**. La source de données est créé à l’aide de tous les attributs spécifiés sur cette offre et autres écrans de l’Assistant, et vous ont la possibilité de tester la source de données qui vient d’être créé.

## <a name="next-steps"></a>Étapes suivantes

[Assistant Source de données, écran 3](../../../connect/odbc/windows/dsn-wizard-3.md)
