---
reusableId: 110
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Tenants
id: 70B-79M2-SF8-1QC
slug: tenants
isVisible: true
lastUpdated: '2025-10-15 15:29:46'
---
# **<span align="center">Tenants</span>**

<span align="justify">Each tenant gets access to a dedicated portal with real-time insights into only the data and dashboards you grant them. You can spin up portals for individual customers to add value and reduce churn—or create internal tenants for different teams within your organization.</span>

The following sections describe how to configure tenants in the **Admin → Tenants** view.

## **Create or Edit a Tenant**

1.  Navigate to **Admin → Tenants**.
2.  Click **Add Tenant** (or select an existing tenant and click **Edit**).

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/HIHzXeA0eG2pbKEscM0o.png" alt="Tenants List"></figure>

## **Tenant Details**

Set the basic metadata for your tenant:

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th></tr><tr><td><p><strong>Name</strong></p></td><td><p>A short, unique identifier for the tenant portal.</p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Optional free-form text to describe the tenant’s use case or owner.</p></td></tr><tr><td><p><strong>Created At</strong></p></td><td><p>Read-only timestamp of when the tenant was created.</p></td></tr><tr><td><p><strong>Last Updated</strong></p></td><td><p>Read-only timestamp of the most recent change.</p></td></tr></tbody></table>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/pIzzq6INndPRg146y6jW.png" alt="Tenant Details" align="center"></figure>

<br />

## **Sets Config**

Control which data sources each tenant can see, and at what level of access:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/EOyfjyu3GxPhoRcWTrVb.png" alt="Tenant Sets Config" align="center"></figure>

<br />

<table><tbody><tr><th><p>Column</p></th><th><p>Meaning</p></th></tr><tr><td><p><strong>↕ Move</strong></p></td><td><p>Drag or click to reorder how data sets appear in the tenant portal.</p></td></tr><tr><td><p><strong>Set</strong></p></td><td><p>Name of the data source or dashboard (e.g. “DPI Records”, “NetFlow Metrics”).</p></td></tr><tr><td><p><strong>Access</strong></p></td><td><p>Select one of:<br>- <strong>Full</strong>: tenant can view, query, and export.<br>- <strong>Partial</strong>: tenant only sees filtered subset (requires <strong>Field</strong>, <strong>Type</strong>, and <strong>Values</strong>).<br>- <strong>None</strong>: hidden.</p></td></tr><tr><td><p><strong>Field</strong></p></td><td><p><em>(Only if Partial)</em> The schema field used to partition data (e.g. <code>customer_id</code>, <code>region</code>).</p></td></tr><tr><td><p><strong>Type</strong></p></td><td><p><em>(Only if Partial)</em> Choose one:<br>- <code>IP</code> (single address)<br>- <code>IP Range</code> (e.g. <code>10.0.0.1-10.0.0.255</code>)<br>- <code>Subnet</code> (e.g. <code>192.168.1.0/24</code>)<br>- <code>Identifier</code> (decorated database field).</p></td></tr><tr><td><p><strong>Values</strong></p></td><td><p><em>(Only if Partial)</em> Comma-separated list of allowed values, matching the <strong>Type</strong>.</p></td></tr></tbody></table>

> **Note:** When you choose **Identifier** as the field type, you’re referring to a “decorated” column in the database—one that’s been generated or enriched by the Visual Smart Data Broker. For more on how these decorator fields work (and how to configure them), see the **V.S. Data Broker** chapter.
> 
> **Pro Tip:** Checking the top-row **Access** checkbox applies that permission to _all_ data sets. Don’t forget to click **Save Changes** at the bottom of the page!

## <br />
**Tenant Users**

This section lists which users belong to this tenant.<br />
To add or remove users, go to **Admin → Users**, select a user, and assign them to the desired tenant.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/okym54ss97OzUoFtryn4.png" alt="Tenant Users"></figure>

<div class="sd-callout" data-callout-type="tip">Tip: Always click <strong>Save Changes</strong> after modifying any tenant settings.</div>

<br />