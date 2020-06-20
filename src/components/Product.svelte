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

    import Noty from "noty"
    import {onMount} from "svelte"


    let listProduct = [
        {id: 1, name: "laptop toshiba", description: "is a laptop", category: "laptops"},
        {id: 2, name: "table ianix", description: "is a table", category: "tables"},
    ]

    onMount(()=>{
        new Noty({
            text:"Iniciaiando",
            theme:"mint",
            timeout:3000

        }).show()
    })


    let product = {
        id: "",
        name: "",
        imageUrl:"",
        description: "",
        category: ""
    }


    const productFindById=(id)=>{
        let index=listProduct.findIndex(producto=>producto.id==id)
         product=listProduct[index]

        console.log(product)
    }

    const editProduct=()=>{
        let index=listProduct.findIndex(product=>product.id===product.id)
        listProduct[index]=product;
        limpiar()
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

   const saveProduct=e=>{
       let newProduct={
           id:listProduct.length+1,
           name:product.name,
           description:product.description,
           category:product.category,
           imageUrl:product.imageUrl
       }
       listProduct=listProduct.concat(newProduct)
       limpiar();
   }

    const onSubmitHandle = e => {
        console.log(product.id)
        if (product.id!=="")editProduct()
        else saveProduct()
        e.preventDefault()
    }
</script>

<style>

</style>

    <div class="mt-2 container-fluid">
        <Row>
            <Col sm="4" xs="6" md="6">
                <Card>
                    <CardHeader>
                        <CardTitle><h6>Registro Productos</h6></CardTitle>
                    </CardHeader>
                    <CardBody>
                        <Form on:submit={onSubmitHandle}>
                            <FormGroup>
                                <Label>Product name</Label>
                                <Input

                                        name="productName"
                                        bind:value={product.name} />
                            </FormGroup>
                            <FormGroup>
                                <Label>Product description</Label>
                                <Input
                                        bind:value={product.description}

                                        name="productDescription" />
                            </FormGroup>
                            <FormGroup>
                                <Label>imageProduct</Label>
                                <Input type="url"

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
            <Col sm="6" xs="6" md="6">
                <div style="overflow: auto!important;max-height: 500px">
                {#each listProduct as item  }
                    <Card class="mt-1">
                        <CardBody>
                            <Row>
                                <Col sm="4">
                                    {#if !item.imageUrl}
                                        <img src="img/notProduct.jps" alt="30" class="img-fluid p-2">
                                    {:else}
                                        <img src="{item.imageUrl}" alt="30" class="img-fluid p-2">
                                    {/if}
                                </Col>
                                <Col sm="8">
                                    <h6 class="mb-1">
                                        <strong>{item.name}</strong><br>
                                        <small>{item.category}</small>
                                    </h6>
                                    <span class="card-text "><small>{item.description}</small> </span><br>
                                    <button class="btn-dark btn-sm" on:click={productFindById(item.id)}>edit</button>
                                    <button class="btn-danger btn-sm" on:click={deleteProduct(item.id)}>delete</button>
                                </Col>
                            </Row>
                        </CardBody>
                    </Card>
                {/each}
                </div>
            </Col>
        </Row>
    </div>

