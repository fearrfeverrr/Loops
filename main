init = function()
  game_progress = 0
  game_tasks = 1
  game_completion = 0
  space_pressed_this_frame = false
  
  world = object
    tile_size = 32
    columns_per_map = 25
    rows_per_map = 15
    maps_wide = 2
    maps_high = 2
  end
  world.map_width = world.tile_size * world.columns_per_map
  world.map_height = world.tile_size * world.rows_per_map
  world.draw_width = world.map_width * world.maps_wide
  world.draw_height = world_map_height * world.maps_high
  
  world.x_off = world.map_width/2
  world.y_off = world.map_height/2
  
  initPlayer()
  initInventory()
  initCamera()
  initMinimap()
  initMessages()
  initCollectibles()
  initNpcs()
end

update = function()
  space_pressed_this_frame = false
  game_completion = floor(game_progress / game_tasks * 100)
  
  updateMinimap()
  if minimap.active then
    help.printMapMouseClicks(world.draw_width/screen.width, world.draw_height/screen.height)
    else
      if messages.length == 0 then
        updatePlayer()
      end
      updateCollectibles()
      updateNpcs()
      updateInventory()
      updateCamera()
      help.printMouseClicks()
  end
  updateMessages()
end
 
draw = function()
  screen.clear()
  if minimap.active then
    drawMinimap()
    else
      // todo: only draw maps when on screen
      // top left
      screen.drawMap("top_left_back", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      screen.drawMap("top_left_fore", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      // top right
      screen.drawMap("top_right_back", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      screen.drawMap("top_right_fore", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      // bottom left
      screen.drawMap("bottom_left_back", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      screen.drawMap("bottom_left_fore", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      // bottom right
      screen.drawMap("bottom_right_back", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      screen.drawMap("bottom_right_fore", -camera.x-world.x_off, -camera.y-world.y_off, world.map_width, world.map_height)
      
      drawCollectibles()
      drawNpcs()
      drawPlayer()
      drawInventory()
      drawMessages()
  end
  
  // draw game info
  locals col = "rbga(255,255,255,0.8)"
  if not minimap.active then
    screen.fillRect(0, -92, screen.width, 16, "rbga(0, 0, 0, 0.4)")
    screen.setFont("NosiferSans")
    screen.setDrawAnchor(-1, 0)
    if inventory.displaying then
      screen.drawText("Press 'E' to close", -170, -92, 5, col)
      else
        screen.drawText("Press 'I' for inventory", -170, -92, 5, col)
    end
    if minimap.actie then
      screen.drawText("Press 'M' to exit map", -40, -92, 5, col)
      else
        screen.drawText("Press 'M' for map", -40, -92, 5, col)
    end
    screen.drawText("Game completion: " + game_completion + "%", 70, -92, 5, col)
    screen.setDrawAnchor(0, 0)
  end
      
      
  
  
