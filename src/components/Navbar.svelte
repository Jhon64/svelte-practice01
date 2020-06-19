<script>
    import{Navbar,NavbarBrand,NavbarToggler,Collapse,NavItem,NavLink,UncontrolledDropdown,DropdownToggle,
    DropdownMenu,DropdownItem} from "sveltestrap"

    let isOpen=false;
    let handleUpdate=event=>{
        isOpen = event.detail.isOpen;
    }
</script>
<Navbar color="light" light expand="md" style="width: 100%">
    <NavbarBrand href="/">sveltestrap SVELTE</NavbarBrand>
    <NavbarToggler on:click={() => (isOpen = !isOpen)} />
</Navbar>