---
title: Éditeur de Destination OLE DB (Page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdestadapter.connection.f1
helpviewer_keywords:
- OLE DB Destination Editor
ms.assetid: ae2200c6-8ba0-49b7-b01a-53425b84d2ed
caps.latest.revision: 81
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1e6aaff0e415aeaab5e42395a3acd7c0b96a0f00
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328069"
---
# <a name="ole-db-destination-editor-connection-manager-page"></a>Éditeur de destination OLE DB (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination OLE DB** pour sélectionner la connexion OLE DB de la destination. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
> [!NOTE]  
>  Le `CommandTimeout` propriété de la destination OLE DB n’est pas disponible dans le **éditeur de Destination OLE DB**, mais peut être définie à l’aide de la **éditeur avancé**. De plus, certaines options de chargement rapide sont uniquement disponibles dans **l’Éditeur avancé**. Pour plus d’informations sur ces propriétés, consultez la section sur la destination OLE DB dans [Propriétés personnalisées OLE DB](data-flow/ole-db-custom-properties.md).  
  
 Pour en savoir plus sur la destination OLE DB, consultez [OLE DB Destination](data-flow/ole-db-destination.md).  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** .  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de chargement des données dans la destination. Le chargement de données du jeu de caractères codés sur deux octets (DBCS) nécessite l'utilisation d'une des options de chargement rapide. Pour plus d’informations sur les modes d’accès aux données à chargement rapide, qui sont optimisés pour les insertions en bloc, consultez [Destination OLE DB](data-flow/ole-db-destination.md).  
  
|Option|Description|  
|------------|-----------------|  
|Table ou vue|Chargez les données dans une table ou une vue de la destination OLE DB.|  
|Table ou vue - chargement rapide|Chargez les données dans une table ou une vue de la destination OLE DB et utilisez l'option de chargement rapide. Pour plus d’informations sur les modes d’accès aux données à chargement rapide, qui sont optimisés pour les insertions en bloc, consultez [Destination OLE DB](data-flow/ole-db-destination.md).|  
|Variable de nom de table ou de vue|Spécifiez le nom de la table ou de la vue dans une variable.<br /><br /> **Informations connexes**: [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)|  
|Variable de nom de table ou de vue - chargement rapide|Spécifiez le nom de la table ou de la vue dans une variable et chargez les données à l'aide de l'option de chargement rapide. Pour plus d’informations sur les modes d’accès aux données à chargement rapide, qui sont optimisés pour les insertions en bloc, consultez [Destination OLE DB](data-flow/ole-db-destination.md).|  
|Commande SQL|Chargez les données dans la destination OLE DB à l'aide d'une requête SQL.|  
  
 **Aperçu**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Visualiser les résultats de la requête** . L'aperçu peut afficher jusqu'à 200 lignes.  
  
## <a name="data-access-mode-dynamic-options"></a>Options dynamiques du mode d'accès aux données  
 Chacun des paramètres **Mode d’accès aux données** affiche un jeu dynamique d’options spécifiques au paramètre en question. Les sections suivantes décrivent chacune des options dynamiques disponibles pour chaque paramètre **Mode d’accès aux données** .  
  
### <a name="data-access-mode--table-or-view"></a>Mode d'accès aux données = Table ou vue  
 **Nom de la table ou de la vue**  
 Sélectionnez le nom de la table ou de la vue dans la liste de celles qui sont disponibles dans la source de données.  
  
 **Nouveau**  
 Utilisez la boîte de dialogue **Créer une table** pour créer une table.  
  
> [!NOTE]  
>  Quand vous cliquez sur **Nouvelle**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] génère une instruction CREATE TABLE par défaut, basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table**. Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
### <a name="data-access-mode--table-or-view--fast-load"></a>Mode d'accès aux données = Table ou vue - chargement rapide  
 **Nom de la table ou de la vue**  
 Sélectionnez une table ou une vue dans la base de données à l’aide de cette liste, ou créez une table en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Utilisez la boîte de dialogue **Créer une table** pour créer une table.  
  
> [!NOTE]  
>  Quand vous cliquez sur **Nouvelle**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] génère une instruction CREATE TABLE par défaut, basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table**. Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Conserver l'identité**  
 Spécifiez si les valeurs d'identité doivent être copiées lors du chargement des données. Cette propriété n'est disponible qu'avec l'option de chargement rapide. La valeur par défaut de cette propriété est `false`.  
  
 **Conserver les valeurs NULL**  
 Spécifiez si les valeurs NULL doivent être copiées lors du chargement des données. Cette propriété n'est disponible qu'avec l'option de chargement rapide. La valeur par défaut de cette propriété est `false`.  
  
 **Verrou de table**  
 Spécifiez si la table est verrouillée pendant le chargement. La valeur par défaut de cette propriété est `true`.  
  
 **Contraintes de validation**  
 Spécifiez si la destination vérifie les contraintes lors du chargement des données. La valeur par défaut de cette propriété est `true`.  
  
 **Lignes par lot**  
 Permet d'indiquer le nombre de lignes contenues dans un traitement. La valeur par défaut de cette propriété est **–1**, ce qui signifie qu’aucune valeur n’a été attribuée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination OLE DB** pour indiquer que vous ne voulez pas assigner de valeur personnalisée à cette propriété.  
  
 **Taille de validation d'insertion maximale**  
 Spécifiez la taille du lot que la destination OLE DB tente de valider pendant les opérations de chargement rapide. La valeur **0** indique que toutes les données sont validées dans un seul lot après traitement de toutes les lignes.  
  
> [!NOTE]  
>  Une valeur de **0** peut faire en sorte que le package en cours d’exécution cesse de répondre si la destination OLE DB et un autre composant de flux de données mettent à jour la même table source. Pour empêcher que le package ne s’arrête, affectez la valeur **2147483647** à l’option **Taille de validation d’insertion maximale**.  
  
 Si vous spécifiez une valeur pour cette propriété, la destination valide les lignes par lot qui ont la plus petite taille entre (a) la **Taille de validation d’insertion maximale**et (b) les lignes restantes dans le tampon qui sont en cours de traitement.  
  
> [!NOTE]  
>  Tout échec de contrainte à la destination entraîne l’échec de la totalité du lot de lignes définies par la **Taille de validation d’insertion maximale** .  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le nom de la table ou de la vue.  
  
### <a name="data-access-mode--table-name-or-view-name-variable--fast-load"></a>Mode d'accès aux données = Variable de nom de table ou de vue - chargement rapide  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le nom de la table ou de la vue.  
  
 **Nouveau**  
 Utilisez la boîte de dialogue **Créer une table** pour créer une table.  
  
> [!NOTE]  
>  Quand vous cliquez sur **Nouvelle**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] génère une instruction CREATE TABLE par défaut, basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table**. Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Conserver l'identité**  
 Spécifiez si les valeurs d'identité doivent être copiées lors du chargement des données. Cette propriété n'est disponible qu'avec l'option de chargement rapide. La valeur par défaut de cette propriété est `false`.  
  
 **Conserver les valeurs NULL**  
 Spécifiez si les valeurs NULL doivent être copiées lors du chargement des données. Cette propriété n'est disponible qu'avec l'option de chargement rapide. La valeur par défaut de cette propriété est `false`.  
  
 **Verrou de table**  
 Spécifiez si la table est verrouillée pendant le chargement. La valeur par défaut de cette propriété est `false`.  
  
 **Contraintes de validation**  
 Spécifiez si la tâche vérifie les contraintes. La valeur par défaut de cette propriété est `false`.  
  
 **Lignes par lot**  
 Permet d'indiquer le nombre de lignes contenues dans un traitement. La valeur par défaut de cette propriété est **–1**, ce qui signifie qu’aucune valeur n’a été attribuée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination OLE DB** pour indiquer que vous ne voulez pas assigner de valeur personnalisée à cette propriété.  
  
 **Taille de validation d'insertion maximale**  
 Spécifiez la taille du lot que la destination OLE DB tente de valider pendant les opérations de chargement rapide. La valeur par défaut, **2147483647** , indique que toutes les données sont validées dans un seul lot après traitement de toutes les lignes.  
  
> [!NOTE]  
>  Une valeur de **0** peut faire en sorte que le package en cours d’exécution cesse de répondre si la destination OLE DB et un autre composant de flux de données mettent à jour la même table source. Pour empêcher que le package ne s’arrête, affectez la valeur **2147483647** à l’option **Taille de validation d’insertion maximale**.  
  
### <a name="data-access-mode--sql-command"></a>Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte d’une requête SQL, générez la requête en cliquant sur **Générer une requête**ou recherchez le fichier qui contient le texte de la requête en cliquant sur **Parcourir**.  
  
> [!NOTE]  
>  La destination OLE DB ne prend pas en charge les paramètres. Si vous devez exécuter une instruction INSERT paramétrable, envisagez d'utiliser la transformation de commande OLE DB. Pour plus d’informations, consultez [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md).  
  
 **Construire une requête**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , localisez le fichier qui contient le texte de la requête SQL.  
  
 **Analyser la requête**  
 Vérifiez la syntaxe du texte de la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de Destination OLE DB &#40;Page mappages&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md)   
 [Éditeur de Destination OLE DB &#40;Page sortie d’erreur&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md)   
 [Charger des données à l’aide de la destination OLE DB](data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  
