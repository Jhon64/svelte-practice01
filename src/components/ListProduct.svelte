<script>
    export let listProduct;
    export let product;
    import {Card,CardBody,Col,CardText,Row} from "sveltestrap"

    const editProduct=(id)=>{
        console.log(id)
    }

    const deleteProduct=(id)=>{
        listProduct=listProduct.filter(product=>product.id!==id)
    }
</script>

                {#each listProduct as item  }
                <Card class="mt-1">
                        <CardBody>
                            <Row>
                            <Col sm="4">

                                {#if !item.imageUrl}
                                    <img src="img/notProduct.jps" alt="50" class="img-fluid p-2">
                                    {:else}
                                    <img src="{item.imageUrl}" alt="50" class="img-fluid p-2">
                                    {/if}
                            </Col>
                            <Col sm="8">
                                <h6 class="">
                                   <strong>{item.name}</strong><br>
                                    <small>{item.category}</small>
                                </h6>
                                <p class="card-text "><small>{item.description}</small> </p>
                                <button class="btn-dark btn-sm" on:click={editProduct(item.id)}>edit</button>
                                <button class="btn-danger btn-sm" on:click={deleteProduct(item.id)}>delete</button>
                            </Col>
                            </Row>
                        </CardBody>
                </Card>
                {/each}

<style></style>