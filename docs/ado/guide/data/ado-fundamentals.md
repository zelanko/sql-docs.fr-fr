---
title: Principes de base ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d6a66928-e68f-4c38-b87a-838c5de50a28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 448eda8c3c77f410bedd88d1193f2302c926ee95
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062925"
---
# <a name="ado-fundamentals"></a>Concepts de base d’ADO
ADO offre aux développeurs un modèle objet logique puissantes pour accéder par programmation aux, la modification et la mise à jour des données à partir d’un large éventail de sources de données via les interfaces système OLE DB. L’utilisation d’ADO la plus courante consiste à interroger une table ou des tables dans une base de données relationnelle, récupérer et afficher les résultats dans une application et permettre aux utilisateurs de peut-être apporter et enregistrer les modifications apportées aux données. Autres tâches sont les suivantes :  
  
-   Interrogation d’une base de données à l’aide de SQL et afficher les résultats.  
  
-   L’accès aux informations dans un magasin de fichiers sur Internet.  
  
-   Manipulation des messages et des dossiers dans un système de messagerie.  
  
-   L’enregistrement des données à partir d’une base de données dans un fichier XML.  
  
-   L’exécution des commandes décrites avec XML et la récupération d’un flux XML.  
  
-   L’enregistrement des données dans un fichier binaire ou un flux XML.  
  
-   Qui permet à un utilisateur examiner et modifier des données dans les tables de base de données.  
  
-   Création et réutilisation paramétré les commandes de base de données.  
  
-   Exécution de procédures stockées.  
  
-   Créer dynamiquement une structure flexible, qui est nommée un **Recordset**, pour contenir, de parcourir et de manipuler des données.  
  
-   Exécution d’opérations de base de données transactionnelle.  
  
-   Filtrage et tri des copies locales des informations de base de données en fonction de critères de l’exécution.  
  
-   Créer et manipuler des résultats hiérarchiques à partir de bases de données.  
  
-   Champs de base de données de liaison pour les composants prenant en charge les données.  
  
-   Création à distance, déconnecté **Recordsets**.  
  
 ADO expose un large éventail d’options et paramètres pour fournir une telle flexibilité. Par conséquent, il est important d’adopter une approche méthodique pour savoir comment utiliser ADO dans une application, décomposer de chacun de vos objectifs en éléments gérables.  
  
 Quatre opérations principales sont impliquées dans la plupart des applications qui utilisent ADO : obtention de données, examinez les données, modification des données et la mise à jour des données. Ces opérations sont examinées plus en détail plus loin dans cette section.  
  
 Toutefois, avant d’aborder ces détails, nous présenterons une vue d’ensemble du modèle objet ADO et une application ADO simple, ce qui est écrit en Microsoft Visual Basic® et effectue chacune des quatre opérations ADO principales :  
  
-   [Objets et collections ADO](../../../ado/guide/data/ado-objects-and-collections.md)  
  
-   [HelloData : Une Application ADO Simple](../../../ado/guide/data/hellodata-a-simple-ado-application.md)  
  
-   [Fournisseurs OLE DB](../../../ado/guide/data/ole-db-providers-ado.md)  
  
-   [Erreurs](../../../ado/guide/data/errors-ado.md)
