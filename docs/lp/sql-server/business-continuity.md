---
layout: HubPage
hide_bc: true
title: Continuité de l’activité SQL Server
description: Explorez les différentes fonctionnalités de SQL Server pour la haute disponibilité, la récupération d’urgence et la continuité de votre activité, quelles que soient les circonstances.
ms.topic: hub-page
ms.prod: sql
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.date: 12/15/2018
featureFlags:
- clicktale
ms.openlocfilehash: 8d0ffb00e47f24fdd8ba85b7dee03119b67c9d0f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63264993"
---
<div id="main" class="v2">
    <div class="container">
        <ul class="cardsY panelContent featuredContent">
            <li>
                <a href="https://www.microsoft.com/evalcenter/evaluate-sql-server-2019-ctp">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-sql-server.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Essayer SQL Server 2019 (préversion)</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/get-azure-sql-vm.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Obtenir une machine virtuelle avec SQL Server</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="/sql/ssms/download-sql-server-management-studio-ssms">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-ssms.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Télécharger SQL Server Management Studio</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>              
        </ul>
    </div>
    <div class="container">
        <h1>Continuité de l’activité</h1>
        <ul class="pivots tabLess">
            <li class="pivotItem" style="display: list-item;" data-id="#products">
                <a href="#products" data-linktype="self-bookmark"></a>
                <ul id="products">
                    <li class="panelItem" data-index="0">
                        <a class="singlePanelNavItem selected" href="#products1" data-linktype="self-bookmark"></a>
                        <ul class="cardsD panelContent singlePanelContent" id="products1" style="margin-top: 0px; display: flex;">
                            <li>
                                <a href="/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/availability-groups.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Groupes de disponibilité Always On</h3>
                                                    <p>Disponibilité élevée au niveau de la base de données, où les instances indépendantes hébergent les bases de données qui sont des réplicas les unes des autres, hébergées sur des clusters de basculement, et qui permettent le déchargement de requêtes en lecture seule vers les réplicas secondaires</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/failover-cluster.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Instances de cluster de basculement Always On</h3>
                                                    <p>Disponibilité élevée au niveau de l’instance, où une seule instance se trouve entre deux ou plusieurs clusters de basculement Windows</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/database-engine/database-mirroring/database-mirroring-sql-server">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/db-mirroring.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Mise en miroir de bases de données</h3>
                                                    <p>Disponibilité élevée au niveau de la base de données qui permet le basculement, ne nécessite pas de cluster de basculement, peut décharger la création de rapports avec l’utilisation de captures instantanées de base de données</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/database-engine/log-shipping/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/log-shipping.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Copie des journaux de transaction</h3>
                                                    <p>Fonctionnalité qui envoie automatiquement des sauvegardes des journaux de transactions à un serveur secondaire de secours. </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/backup-restore.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Sauvegarde et restauration</h3>
                                                    <p>Composant qui apporte une sécurité essentielle pour la protection des données cruciales stockées dans SQL Server.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/logs/the-transaction-log-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/t-log-mgmt.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Gestion des journaux de transactions</h3>
                                                    <p>Concept qui facilite la récupération des données en cas de sinistre.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                        </ul>
                    </li>
                </ul>
            </li>
        </ul>
    </div>
<div class="container centered pageFooter">
        <h2>Restez en contact avec nous</h2>
        <ul class="links">
           <li>
                <a href="https://aka.ms/editsqldocs" data-linktype="external"> Collaborer </a>
            </li>
           <li>
                <a href="https://docs.microsoft.com/sql/sql-server/sql-server-get-help" data-linktype="external"> Obtenir de l’aide </a>
            </li>
           <li>
                <a href="https://aka.ms/sqldocsfeedback" data-linktype="external"> Commentaires </a>
            </li>
           <li>
                <a href="https://aka.ms/sqldocsurvey" data-linktype="external"> Enquête </a>
            </li>
           <li>
                <a href="https://cloudblogs.microsoft.com/sqlserver/" data-linktype="external"> Blog </a>
            </li>
            <li>
                <a href="https://twitter.com/sqldocs" data-linktype="external"> Twitter </a>
            </li>
            <li>
                <a href="https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqldatabaseengine&filter=alltypes&sort=lastpostdesc" data-linktype="external"> Forum MSDN </a>
            </li>
            <li>
                <a href="https://feedback.azure.com/forums/908035-sql-server" data-linktype="external"> User Voice </a>
            </li>
        </ul>
    </div>