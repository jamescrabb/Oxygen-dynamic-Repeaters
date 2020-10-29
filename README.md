# Oxygen-dynamic-Repeaters
Related Child Posts

// Related Child Posts
<?php
function dynamic_child_post_query( $query ) {
  global $post;
  if ( $query->query['post_type'][0] == 'pumps' ) {
    $query->set( 'orderby', 'rand' ); /* Here you can change order */
    $query->set( 'post__not_in', array($post->ID) ); /* Not including the current post */
     $query->set( 'post_parent', $post->post_parent ); /* Looks for the child posts of parent */
    $query->set( 'no_found_rows', true ); /* Delete this if you need pagination */
  }
}
add_action( 'pre_get_posts', 'dynamic_child_post_query' );
?>
