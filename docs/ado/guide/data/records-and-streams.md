---
title: Enregistrements et flux | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- streams [ADO]
- streams [ADO], about streams
- records [ADO]
ms.assetid: 4d68868e-2611-4b5c-9a89-7caa5f753151
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 19fc6e61a10e1a92f0f674a23d00f1e1b06a596c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701698"
---
# <a name="records-and-streams"></a>Enregistrements et flux
ADO fournit actuellement la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet en tant que le principal moyen d’accéder aux informations dans les sources de données, telles que des bases de données relationnelles. Toutefois, certains fournisseurs prennent en charge la [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) et [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objets en tant qu’objets alternatifs ou complémentaires manipuler les données provenant de fournisseurs. Pour obtenir des détails sur **enregistrement** comportement, consultez la documentation de votre fournisseur.  
  
## <a name="records"></a>Enregistrements  
 **Enregistrement** objets fonctionnent essentiellement comme une seule ligne **Recordset**s. Toutefois, **enregistrements** ont des fonctionnalités par rapport à limitées **Recordsets** et ils ont différentes propriétés et méthodes. La source des données dans un **enregistrement** objet peut être une commande qui retourne une ligne de données à partir du fournisseur. À l’aide de **enregistrement** objets plutôt que **Recordset** objets pour recevoir les résultats d’une requête qui retourne une ligne de données élimine la surcharge de l’instanciation plus complexe **Recordset**  objet.  
  
 **Enregistrement** objets peuvent servir à une autre utilisation, surtout avec des fournisseurs pour les sources de données autres que les bases de données relationnelles traditionnelles, telles que la [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). La plupart des informations qui doivent être traitées existe, pas en tant que tables dans les bases de données, mais en tant que messages dans les systèmes de messagerie électronique et les fichiers dans les systèmes de fichiers modernes. Le **enregistrement** et **Stream** objets facilitent l’accès aux informations stockées dans des sources autres que des bases de données relationnelles.  
  
 Le **enregistrement** objet peut représenter et gérer des données telles que les fichiers et répertoires d’un système de fichiers ou des dossiers et des messages dans un système de messagerie. À ces fins, la source pour le **enregistrement** peut être la ligne actuelle d’ouvert **Recordset**, une URL absolue ou une URL relative en association avec une ouverture [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
 En règle générale, un **Recordset** peut être utilisé pour représenter un conteneur ou un parent dans une hiérarchie comme un dossier ou un répertoire. Un **enregistrement** peut être utilisé pour retourner des informations spécifiques sur un seul nœud dans le conteneur parent, tel qu’un fichier ou d’un document. La raison principale **enregistrements** sont utilisés pour représenter ce type d’information est que ces sources de données sont hétérogènes. Cela signifie que chaque **enregistrement** peut avoir un autre jeu et le nombre de champs. Traditionnel **Recordsets** contenant des lignes à partir d’une base de données sont homogènes, ce qui signifie que chaque ligne a le même nombre et le type de champs.  
  
 Pour plus d’informations sur l’utilisation de la **enregistrement** d’objets pour le traitement des données hétérogènes de fournisseurs tels que le fournisseur de publication Internet, consultez [à l’aide d’ADO pour la publication Internet](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
## <a name="streams"></a>flux de données  
 Le **Stream** objet fournit les moyens de lire, écrire et gérer un flux d’octets. Ce flux d’octets peut être du texte ou binaire et la taille est limité uniquement par les ressources système. En règle générale, ADO **Stream** objets sont utilisés aux fins suivantes :  
  
-   Pour contenir les données d’un **Recordset** enregistré au format XML. Ces flux de données XML à partir d’enregistré **Recordset**s peut être utilisé comme source lorsque vous ouvrez un nouveau **Recordset**. Pour plus d’informations, consultez [flux et persistance](../../../ado/guide/data/streams-and-persistence.md).  
  
-   Pour contenir [CommandStreams](../../../ado/reference/ado-api/commandstream-property-ado.md) pour être exécutée sur le fournisseur comme alternative à [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md). Par exemple, les codes XML utilisable comme source pour une commande sur le fournisseur Microsoft OLE DB pour SQL Server.  
  
-   Pour recevoir les résultats à partir du fournisseur dans un format autre qu’un **Recordset**, telles que les résultats XML à partir du fournisseur Microsoft OLE DB pour SQL Server. Pour plus d’informations, consultez [récupération de jeux de résultats en flux](../../../ado/guide/data/retrieving-resultsets-into-streams.md).  
  
-   Pour contenir le texte ou les octets qui composent un fichier ou un message, généralement utilisés avec les fournisseurs tels que le fournisseur Microsoft OLE DB pour Internet Publishing. Pour plus d’informations sur cette utilisation de **Stream** , consultez [à l’aide d’ADO pour la publication Internet](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
 Un **Stream** objet peut être ouvert sur :  
  
-   Un simple fichier spécifié avec une URL.  
  
-   Un champ d’un **enregistrement** ou **Recordset** contenant un **Stream** objet.  
  
-   Le flux par défaut d’un **enregistrement** ou **Recordset** objet représentant un répertoire ou un fichier composé.  
  
-   Un champ de ressources contenant l’URL d’un fichier simple.  
  
-   Aucune source particulier du tout. Dans ce cas, un **Stream** objet est ouvert en mémoire. Données peuvent être écrites et puis enregistrées dans un autre **Stream** ou fichier.  
  
-   Un champ d’objet BLOB dans un **Recordset**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Flux et persistance](../../../ado/guide/data/streams-and-persistence.md)  
  
-   [Flux de commandes](../../../ado/guide/data/command-streams.md)  
  
-   [Récupération de jeux de résultats dans les flux](../../../ado/guide/data/retrieving-resultsets-into-streams.md)  
  
-   [Utilisation d’ADO pour la publication Internet](../../../ado/guide/data/using-ado-for-internet-publishing.md)
