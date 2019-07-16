---
title: Wide World Importers - base de données exemple SQL | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c178d116dddb5dc18b1bec91066205fe08f6d0c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067610"
---
# <a name="wide-world-importers-sample-databases-for-microsoft-sql"></a>Wide World Importers exemples de bases de données pour Microsoft SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Il s’agit d’une vue d’ensemble de la société fictive Wide World Importers et les flux de travail qui est abordés dans les bases de données exemple WideWorldImporters pour SQL Server et de la base de données SQL Azure.  

Wide World Importers (WWI) est un importateur de marchandises fantaisie en gros et le serveur de distribution d’exploitation à partir de la zone de la baie de San Francisco.

Comme un grossiste, les clients de WWI sont principalement les entreprises qui revendent à des individus. WWI vend aux clients de vente au détail des États-Unis, y compris les magasins spécialisés, supermarchés, magasins, les magasins d’attraction de tourisme et certaines personnes l’informatique. WWI vend également aux autres grossistes via un réseau d’agents qui encouragent les produits procuration de WWI. Tous les clients de WWI sont actuellement basés aux États-Unis, la société a l’intention de transmission pour l’extension à dans d’autres pays.

WWI achète des marchandises auprès des fournisseurs, y compris la nouveauté et des fabricants de jouets et autres grossistes fantaisie. Ils boursiers les marchandises dans leur entrepôt de WWI et la réorganisation de fournisseurs en fonction des besoins de satisfaire aux demandes du client. Ils également acheter des volumes importants d’empaquetage de matériaux et les vendent dans petites quantités pour des raisons pratiques pour les clients.

WWI a récemment démarré des ventes diverses alimentaires attrapes telles que piment fiers.  Précédemment, la société n’avait pas gérer les éléments réfrigérées. Maintenant, pour répondre à gestion des exigences de produits alimentaires, ils doivent surveiller la température dans leur espace de refroidissement et toutes leurs camions qui ont des sections de refroidissement.

## <a name="workflow-for-warehouse-stock-items"></a>Flux de travail pour les articles de stock d’entrepôt

Le flux général de la façon dont les éléments sont stockés et distribués est comme suit :
- WWI crée des bons de commande et envoie les commandes aux fournisseurs.
- Les éléments d’envoi de fournisseurs, WWI les reçoit et les stocke dans leur magasin.
- Éléments de commande des clients à partir de WWI
- WWI remplit la commande du client avec les éléments de stock de l’entrepôt, et lorsqu’ils n’ont pas suffisamment stock, ils commandent le stock supplémentaire auprès de fournisseurs.
- Certains clients ne souhaitent pas attendre que les éléments qui ne sont pas en stock. Si suivant leur ordre disons cinq différents articles en stock et quatre sont disponibles, ils souhaitent recevoir les quatre éléments en souffrance de l’élément restant. L’élément sera donc les envoyé plus loin dans un colis séparé.
- WWI les factures clients pour les articles en stock, généralement en convertissant la commande en facture.
- Les clients peuvent commander des éléments qui ne sont pas en stock. Ces éléments sont en cours d’approvisionnement.
- WWI fournit des articles en stock aux clients via leurs propres RVA de remise, ou autres courriers ou les méthodes de transport.
- Les clients paient les factures à WWI.
- Périodiquement, WWI paie des fournisseurs pour les éléments qui se trouvaient sur les bons de commande. Il s’agit souvent un certain temps après que qu’ils ont reçu les marchandises.

## <a name="data-warehouse-and-analysis-workflow"></a>Flux de travail entrepôt et d’analyse de données

Bien que l’équipe WWI utiliser SQL Server Reporting Services pour générer des rapports opérationnels à partir de la base de données WideWorldImporters, ils doivent également effectuer l’analytique sur leurs données et avez besoin générer des rapports stratégiques. L’équipe ont créé un modèle de données de dimension dans une base de données WideWorldImportersDW. Cette base de données est remplie par un package Integration Services.

SQL Server Analysis Services est utilisé pour créer des modèles de données analytiques à partir des données dans le modèle de données dimensionnelles. SQL Server Reporting Services est utilisé pour générer des rapports stratégiques directement depuis le modèle de données de dimension et également à partir du modèle d’analyse. Power BI est utilisé pour créer des tableaux de bord à partir des mêmes données. Les tableaux de bord est utilisés sur les sites Web et sur les téléphones et tablettes. *Remarque : ces modèles de données et les rapports ne sont pas encore disponibles*

## <a name="additional-workflows"></a>Flux de travail supplémentaires

Il s’agit des flux de travail supplémentaires.
- WWI problèmes avoirs lorsqu’un client ne reçoit pas la bonne pour une raison quelconque, ou lorsque les marchandises sont défectueux. Ceux-ci sont traités comme des factures négatif.
- WWI compte régulièrement les quantités en stock des articles en stock pour vous assurer que les quantités en stock indiquées comme étant disponibles sur son système sont exactes. (Le processus d’effectuer cette opération est appelé d’un inventaire).
- Températures ambiantes à froid. Périssables sont stockés dans des locaux frigorifiques. Données de capteur à partir de ces espaces sont ingérées dans la base de données à des fins de surveillance et analytique.
- Suivi d’un emplacement de véhicule. Véhicules qui transportent des marchandises pour WWI incluent des capteurs qui effectuent le suivi de l’emplacement. Cet emplacement est à nouveau ingéré dans la base de données pour la surveillance et plus analytique.

## <a name="fiscal-year"></a>Année fiscale

La société fonctionne avec un exercice qui commence le 1er novembre.

## <a name="terms-of-use"></a>Conditions d’utilisation

La licence pour la base de données et de l’exemple de code est décrit ici : [license.txt](https://github.com/Microsoft/sql-server-samples/blob/master/license.txt)

La base de données inclut des données publiques qui a été chargées à partir de data.gov et EarthData naturelle. Les conditions d’utilisation se trouvent ici : [https://www.naturalearthdata.com/about/terms-of-use/](https://www.naturalearthdata.com/about/terms-of-use/)
