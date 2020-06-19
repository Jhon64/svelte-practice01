<script>
    import {
        Col,
        Container,
        Row,
        Card,
        CardBody,
        CardHeader,
        CardFooter,
        CardTitle,
        Input,
        Form,
        FormGroup,
        Label,
        Button,
        CardText
    } from "sveltestrap";


    let listProduct = [
        {id: 0, name: "laptop toshiba", description: "is a laptop", category: "laptops"},
        {id: 1, name: "table ianix", description: "is a table", category: "tables"},
    ]


    let product = {
        id: "",
        name: "",
        imageUrl:"",
        description: "",
        category: ""
    };

    const productFindById=(id)=>{
        let product=listProduct.
    }

    const editProduct=(id)=>{
        console.log(id)
    }

    const deleteProduct=(id)=>{
        listProduct=listProduct.filter(product=>product.id!==id)
    }

    const limpiar=e=>{
        product = {
            id: "",
            name: "",
            imageUrl:"",
            description: "",
            category: ""
        };
    }

    const onSubmitHandle = e => {
        let newProduct={
            id:listProduct.length,
            name:product.name,
            description:product.description,
            category:product.category,
            imageUrl:product.imageUrl
        }
        listProduct=listProduct.concat(newProduct)
        limpiar();
        e.preventDefault()
    }
</script>

<style>

</style>

<main>
    <Container class="mt-5">
        <Row>
            <Col sm="6" >
                <Card>
                    <CardHeader>
                        <CardTitle>Registro Productos</CardTitle>
                    </CardHeader>
                    <CardBody>
                        <Form on:submit={onSubmitHandle}>
                            <FormGroup>
                                <Label>Product name</Label>
                                <Input
                                        placeholder="product name"
                                        name="productName"
                                        bind:value={product.name} />
                            </FormGroup>
                            <FormGroup>
                                <Label>Product description</Label>
                                <Input
                                        bind:value={product.description}
                                        placeholder="product description"
                                        name="productDescription" />
                            </FormGroup>
                            <FormGroup>
                                <Label>imageProduct</Label>
                                <Input type="url"
                                       placeholder="productUrl"
                                       name="productUrl"
                                       bind:value={product.imageUrl}/>
                            </FormGroup>
                            <FormGroup>
                                <Label>Product category</Label>
                                <select class="form-control " bind:value={product.category}>
                                    <option value="laptops">Laptops</option>
                                    <option value="Pc's">Pc's</option>
                                    <option value="tables">Tables</option>
                                </select>
                            </FormGroup>
                            <FormGroup>
                                <Button class="btn-success" block size="md" type="submit">save</Button>
                            </FormGroup>
                        </Form>
                    </CardBody>
                </Card>
            </Col>
            <Col sm="6" >


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

            </Col>
        </Row>
    </Container>
</main>
